Flash Infer for arm64

git clone https://github.com/flashinfer-ai/flashinfer.git --recursive


pip install ninja



export TORCH_CUDA_ARCH_LIST="90"


cd flashinfer
pip install --no-build-isolation --verbose .

python -m flashinfer.aot  # Compile AOT kernels
python -m pip install --no-build-isolation --verbose .


