vllm - deploy

```bash
sudo apt update
sudo apt updgrade

sudo apt install python3.12 python3.12-venv python3.12-dev


python3.12 -m venv venv
source venv/bin/activate

pip install torch==2.7.1 torchaudio==2.7.1 torchvision --index-url https://download.pytorch.org/whl/cu128


pip install https://github.com/dwani-ai/vllm-arm64/releases/download/v.0.0.4/vllm-0.10.1.dev0+g6d8d0a24c.d20250726-cp312-cp312-linux_aarch64.whl


vllm serve Qwen/Qwen3-0.6B
```