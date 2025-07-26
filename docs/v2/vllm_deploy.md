vllm - deploy

python3.10 -m venv venv
source venv/bin/activate

pip install torch==2.7.1 torchaudio==2.7.1 torchvision --index-url https://download.pytorch.org/whl/cu128


pip install https://github.com/dwani-ai/vllm-arm64/releases/download/v0.0.1/vllm-0.9.2.dev144+g9206d0ff0.d20250618-cp310-cp310-linux_aarch64.whl



vllm serve Qwen/Qwen3-0.6B