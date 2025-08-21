on-b200

sudo apt update
sudo apt upgrade -y

sudo apt install python3.12 python3.12-venv python3.12-dev -y


python3.12 -m venv venv
source venv/bin/activate

pip install torch==2.7.1 torchaudio==2.7.1 torchvision --index-url https://download.pytorch.org/whl/cu128


pip install vllm


vllm serve deepseek-ai/DeepSeek-V3.1 \
  --trust-remote-code \
  --tensor-parallel-size 8 \
  --enable-expert-parallel \
  --max-model-len 154000 \
  --port 8000