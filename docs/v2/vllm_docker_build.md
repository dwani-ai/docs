Vllm - Docker Build

  - vllm arm64 docker container 
  - https://hub.docker.com/r/dwani/vllm-arm64 
  - docker pull dwani/vllm-arm64:latest


https://docs.vllm.ai/en/latest/deployment/docker.html#building-vllms-docker-image-from-source


DOCKER_BUILDKIT=1 sudo docker build . --target vllm-openai --tag vllm/vllm-openai --file docker/Dockerfile --build-arg torch_cuda_arch_list="" --build-arg max_jobs=8 --build-arg nvcc_threads=2 --platform "linux/arm64"


docker run --runtime nvidia --gpus all \
    -v ~/.cache/huggingface:/root/.cache/huggingface \
    -p 8000:8000 \
    --env "HUGGING_FACE_HUB_TOKEN=<secret>" \
    vllm/vllm-openai <args...>


-- 
Extra
- vllm
 - python -m vllm.entrypoints.openai.api_server --host 0.0.0.0 --port 8000

- openweb-ui

docker run -d \
    --name open-webui \
    -p 3000:8080 \
    -v open-webui:/app/backend/data \
    -e OPENAI_API_BASE_URL=http://0.0.0.0:8000/v1 \
    --restart always \
    ghcr.io/open-webui/open-webui:main

