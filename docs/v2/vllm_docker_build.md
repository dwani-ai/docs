Vllm - Docker Build

  - vllm arm64 docker container 
  - https://hub.docker.com/r/dwani/vllm-arm64 
  - docker pull dwani/vllm-arm64:latest




DOCKER_BUILDKIT=1 sudo docker build . \
  --target vllm-openai \
  --tag vllm/vllm-openai \
  --file docker/Dockerfile \
  --build-arg torch_cuda_arch_list="" \
  --build-arg max_jobs=16 \
  --build-arg nvcc_threads=4 \
  --build-arg VLLM_MAX_SIZE_MB=1000 \
  --platform linux/arm64


sudo docker run --runtime nvidia -it --rm -p 9000:9000    --env "HUGGING_FACE_HUB_TOKEN=$HF_TOKEN"
 slabstech/vllm-openai:latest --model google/gemma-3-4b-it --served-model-name gemma3 --host 0.0.0.0 --port 9000 --gpu-memory-utilization 0.8 --tensor-parallel-size 1 --max-model-len 65536     --dtype bfloat16
 
sudo docker tag vllm/vllm-openai:latest dwani/vllm-openai:latest




https://docs.vllm.ai/en/latest/deployment/docker.html#building-vllms-docker-image-from-source

<!-- 

DOCKER_BUILDKIT=1 sudo docker build . --target vllm-openai --tag vllm/vllm-openai --file docker/Dockerfile --build-arg torch_cuda_arch_list="" --build-arg max_jobs=8 --build-arg nvcc_threads=2 --platform "linux/arm64"


docker run --runtime nvidia --gpus all \
    -v ~/.cache/huggingface:/root/.cache/huggingface \
    -p 8000:8000 \
    --env "HUGGING_FACE_HUB_TOKEN=<secret>" \
    vllm/vllm-openai <args...>



docker run --runtime nvidia --gpus all \
  -v ~/.cache/huggingface:/root/.cache/huggingface \
  -p 8000:8000 \
  --env "HUGGING_FACE_HUB_TOKEN=<your_huggingface_token>" \
  vllm/vllm-openai \
  --model Qwen/Qwen3-0.6B \
  --port 8000  


  sudo docker run --runtime nvidia --gpus all \
  -p 8000:8000 \
  vllm/vllm-openai \
  --model Qwen/Qwen3-0.6B \
  --port 8000

  sudo docker run --gpus all \
  -p 8000:8000 \
  vllm/vllm-openai \
  --model Qwen/Qwen3-0.6B \
  --port 8000

-->
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

  sudo docker run --gpus all \
  -p 8000:8000 \
  vllm/vllm-openai \
  --model Qwen/Qwen3-0.6B \
  --port 8000


--

python3 use_existing_torch.py
DOCKER_BUILDKIT=1 docker build . \
--file docker/Dockerfile \
--target vllm-openai \
--platform "linux/arm64" \
-t vllm/vllm-gh200-openai:latest \
--build-arg max_jobs=66 \
--build-arg nvcc_threads=2 \
--build-arg torch_cuda_arch_list="9.0 10.0+PTX"


https://docs.vllm.ai/en/latest/deployment/docker.html#building-for-arm64aarch64

