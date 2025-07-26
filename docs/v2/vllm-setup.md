vLLM for arm64 
 
- Create vllm library 
```bash

sudo apt-get install build-essential libnuma-dev

sudo apt remove cmake

wget https://github.com/Kitware/CMake/releases/download/v3.31.8/cmake-3.31.8-linux-aarch64.sh
chmod +x cmake-3.31.8-linux-aarch64.sh
sudo ./cmake-3.31.8-linux-aarch64.sh --prefix=/usr/local --exclude-subdir

pip uninstall torch torchvision torchaudio

pip install torch==2.7.1 torchaudio==2.7.1 torchvision --index-url https://download.pytorch.org/whl/cu128



git clone https://github.com/vllm-project/vllm.git

cd vllm

git checkout 6d8d0a24c02bfd84d46b3016b865a44f048ae84b

python use_existing_torch.py 

pip install --upgrade setuptools twine setuptools-scm


pip install -r requirements/cuda.txt
export MAX_JOBS=16
##pip install -vvv -e . --no-build-isolation

VLLM_TARGET_DEVICE=cuda python setup.py bdist_wheel
pip install dist/*.whl
```


- Reference
  - For GH200, GB200 Nvidia GPU
  - Python - vllm arm64 wheel on GitHub 
    - 
