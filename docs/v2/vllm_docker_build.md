Vllm - Docker Build

  - vllm arm64 docker container 
  - https://hub.docker.com/r/dwani/vllm-arm64 
  - docker pull dwani/vllm-arm64:latest


https://docs.vllm.ai/en/latest/deployment/docker.html#building-vllms-docker-image-from-source


# optionally specifies: --build-arg max_jobs=8 --build-arg nvcc_threads=2
DOCKER_BUILDKIT=1 docker build . \
    --target vllm-openai \
    --tag vllm/vllm-openai \
    --file docker/Dockerfile \ 
    --build-arg torch_cuda_arch_list="" \
    --build-arg max_jobs=8 \
    --build-arg nvcc_threads=2 \
    --platform "linux/arm64"