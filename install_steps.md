## Installation Steps 

for arm64/GH200 
```bash
sudo apt update
sudo apt upgrade -y

sudo apt install python3.12 python3.12-venv python3.12-dev poppler-utils -y


python3.12 -m venv venv
source venv/bin/activate

pip install torch==2.7.1 torchaudio==2.7.1 torchvision --index-url https://download.pytorch.org/whl/cu128


pip install https://github.com/dwani-ai/vllm-arm64/releases/download/v.0.0.4/vllm-0.10.1.dev0+g6d8d0a24c.d20250726-cp312-cp312-linux_aarch64.whl



vllm serve RedHatAI/gemma-3-27b-it-FP8-dynamic --served-model-name gemma3 --host 0.0.0.0 --port 9000 --gpu-memory-utilization 0.9 --tensor-parallel-size 1 --max-model-len 98304 --disable-log-requests --dtype bfloat16 --enable-chunked-prefill --enable-prefix-caching --max-num-batched-tokens 8192 --chat-template-content-format openai
```