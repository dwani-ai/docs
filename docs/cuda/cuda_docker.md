
- CUDA - Docker
    - Add daemon.json to /etc/docker
    - https://github.com/dwani-ai/docs/blob/main/files/daemon.json

    - sudo systemctl restart docker

    - sudo docker run --runtime nvidia -it --rm -p 9000:9000 dwani-ai/vllm-arm64

    - vllm serve 
