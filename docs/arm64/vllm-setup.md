vLLM for arm64 
 
- Create vllm library wheel
```bash

sudo apt-get install build-essential libnuma-dev -y

sudo apt remove cmake -y

wget https://github.com/Kitware/CMake/releases/download/v3.31.8/cmake-3.31.8-linux-aarch64.sh
chmod +x cmake-3.31.8-linux-aarch64.sh
sudo ./cmake-3.31.8-linux-aarch64.sh --prefix=/usr/local --exclude-subdir

pip uninstall torch torchvision torchaudio

pip install torch==2.7.1 torchaudio==2.7.1 torchvision --index-url https://download.pytorch.org/whl/cu128



git clone https://github.com/vllm-project/vllm.git

cd vllm


python use_existing_torch.py 

pip install --upgrade setuptools twine setuptools-scm


pip install -r requirements/cuda.txt

export MAX_JOBS=16
export NVCC_THREADS=4
export TORCH_CUDA_ARCH_LIST=""
export VLLM_TARGET_DEVICE=cuda

python setup.py bdist_wheel
pip install dist/*.whl
```

