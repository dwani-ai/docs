vllm - deploy

```bash
sudo apt update
sudo apt upgrade

sudo apt install python3.12 python3.12-venv python3.12-dev


python3.12 -m venv venv
source venv/bin/activate

pip install torch==2.7.1 torchaudio==2.7.1 torchvision --index-url https://download.pytorch.org/whl/cu128

pip install flashinfer-python xformers

pip install https://github.com/dwani-ai/vllm-arm64/releases/download/v.0.0.4/vllm-0.10.1.dev0+g6d8d0a24c.d20250726-cp312-cp312-linux_aarch64.whl



vllm serve google/gemma-3-4b-it --served-model-name gemma3 --host 0.0.0.0 --port 9000 --gpu-memory-utilization 0.4 --tensor-parallel-size 1 --max-model-len 65536     --dtype bfloat16 --disable-log-requests


vllm serve RedHatAI/gemma-3-27b-it-FP8-dynamic --served-model-name gemma3 --host 0.0.0.0 --port 9000 --gpu-memory-utilization 0.4 --tensor-parallel-size 1 --max-model-len 65536    --disable-log-requests


vllm serve google/gemma-3-27b-it --served-model-name gemma3 --host 0.0.0.0 --port 9000 --gpu-memory-utilization 0.4 --tensor-parallel-size 1 --max-model-len 65536     --dtype bfloat16 --disable-log-requests

```
https://docs.vllm.ai/en/latest/configuration/engine_args.html#modelconfig



for 3.10 > 

pip install https://github.com/dwani-ai/vllm-arm64/releases/download/v0.0.5/vllm-0.10.1.dev0+g6d8d0a24c.d20250726-cp310-cp310-linux_aarch64.whl


<!-- 
vllm serve Qwen/Qwen3-0.6B

-->

- RedHatAI/gemma-3-27b-it-FP8-dynamic

<!--
https://cloud.google.com/products/calculator?hl=en&dl=CjhDaVJrT0RVMU1XUmlOUzFpT0RFMkxUUTJPR1V0WWpBNU1DMWhNekUwWXpobU1UYzBaREFRQVE9PRAQGiRGRTdBNzJFMC0wRjI5LTQ1MkMtOTI1Ny1DOTM3OEUwRTY5QzE&e=13802955

>