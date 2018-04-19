# warp-transducer
A fast parallel implementation of RNN Transducer.

## Installation

Install [PyTorch](https://github.com/pytorch/pytorch#installation).

`WARP_CTC_PATH` should be set to the location of a built WarpCTC
(i.e. `libwarpctc.so`).  This defaults to `../build`, so from within a
new warp-ctc clone you could build WarpCTC like this:

```bash
git clone https://github.com/SeanNaren/warp-ctc.git
cd warp-ctc
mkdir build; cd build
cmake ..
make
```

Otherwise, set `WARP_CTC_PATH` to wherever you have `libwarpctc.so`
installed. If you have a GPU, you should also make sure that
`CUDA_HOME` is set to the home cuda directory (i.e. where
`include/cuda.h` and `lib/libcudart.so` live). For example:

```
export CUDA_HOME="/usr/local/cuda"
```

Now install the bindings:
```
cd pytorch_binding
python setup.py install
```

If you try the above and get a dlopen error on OSX with anaconda3 (as recommended by pytorch):
```
cd ../pytorch_binding
python setup.py install
cd ../build
cp libwarpctc.dylib /Users/$WHOAMI/anaconda3/lib
```
This will resolve the library not loaded error. This can be easily modified to work with other python installs if needed.

## Reference
* [Sequence Transduction with Recurrent Neural Networks](https://arxiv.org/abs/1211.3711)
* [Baidu warp-ctc](https://github.com/baidu-research/warp-ctc)
* [Awni implementation of transducer](https://github.com/awni/transducer)

## TODO
* Performance test
* GPU implementation