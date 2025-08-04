xformers

https://github.com/facebookresearch/xformers


pip3 install -U xformers --index-url https://download.pytorch.org/whl/cu128


- build

# (Optional) Makes the build much faster
pip install ninja
# Set TORCH_CUDA_ARCH_LIST if running and building on different GPU types
# NOTE: pytorch must already be installed!
pip install -v --no-build-isolation -U git+https://github.com/facebookresearch/xformers.git@main#egg=xformers
# (this can take dozens of minutes)


