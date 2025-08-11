torch 2.8

curl -LsSf https://astral.sh/uv/install.sh | INSTALLER_DOWNLOAD_URL=https://wheelnext.astral.sh sh
uv venv venv
source venv/bin/activate

uv pip install torch torchvision

pip install vllm
