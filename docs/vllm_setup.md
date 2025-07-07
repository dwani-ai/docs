
- vllm + gemma3 Setup
    - Add daemon.json to /etc/docker
    - https://github.com/dwani-ai/deploy/blob/main/files/daemon.json

    - sudo systemctl restart docker

    - sudo docker run --runtime nvidia -it --rm -p 9000:9000 slabstech/dwani-vllm

    - export HF_TOKEN='my-nsma-is-what'

    - vllm serve google/gemma-3-4b-it --served-model-name gemma3 --host 0.0.0.0 --port 9000 --gpu-memory-utilization 0.9 --tensor-parallel-size 1 --max-model-len 16384     --dtype bfloat16 


