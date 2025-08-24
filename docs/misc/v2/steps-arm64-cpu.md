sudo apt-get install liblzma-dev

sudo apt-get install libnuma-dev


sudo apt update && sudo apt upgrade -y

sudo apt install -y software-properties-common build-essential zlib1g-dev libncurses5-dev libgdbm-dev libnss3-dev libssl-dev libreadline-dev libffi-dev curl libsqlite3-dev wget llvm libbz2-dev tk-dev


cd /usr/src
sudo wget https://www.python.org/ftp/python/3.12.4/Python-3.12.4.tgz
sudo tar -xf Python-3.12.4.tgz
cd Python-3.12.4

sudo ./configure --enable-optimizations

sudo make -j$(nproc)
sudo make altinstall

python3.12 --version




sudo snap install astral-uv --classic
uv pip install torch torchvision
python use_existing_torch.py 
pip install --upgrade setuptools twine setuptools-scm
pip install -r requirements/cpu.txt


export MAX_JOBS=4
export VLLM_TARGET_DEVICE=cpu

python setup.py bdist_wheel
pip install dist/*.whl
