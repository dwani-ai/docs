
- vllm + gemma3 Setup
    - Add daemon.json to /etc/docker
    - https://github.com/dwani-ai/deploy/blob/main/files/daemon.json

    - sudo systemctl restart docker

    - sudo docker run --runtime nvidia -it --rm -p 9000:9000 slabstech/dwani-vllm

    - export HF_TOKEN='my-nsma-is-what'

    - vllm serve google/gemma-3-4b-it --served-model-name gemma3 --host 0.0.0.0 --port 9000 --gpu-memory-utilization 0.8 --tensor-parallel-size 1 --max-model-len 16384     --dtype bfloat16 




pip install https://github.com/dwani-ai/vllm-arm64/releases/download/v0.0.2/vllm-0.10.0rc3.dev15+g5a19a6c67.d20250724-cp310-cp310-linux_aarch64.whl

vllm serve Qwen/Qwen2.5-1.5B-Instruct