Vllm - Docker Build

- https://hub.docker.com/r/dwani/vllm-arm64 
- docker pull dwani/vllm-arm64:latest

python3 use_existing_torch.py
DOCKER_BUILDKIT=1 sudo docker build . \
--file docker/Dockerfile \
--target vllm-openai \
--platform "linux/arm64" \
-t vllm/vllm-openai:latest \
--build-arg max_jobs=16 \
--build-arg nvcc_threads=4 \
--build-arg VLLM_MAX_SIZE_MB=1000 \
--build-arg torch_cuda_arch_list=""

sudo docker tag vllm/vllm-openai:latest dwani/vllm-arm64:latest


sudo docker run --runtime nvidia -it --rm -p 9000:9000 dwani/vllm-openai:latest --model RedHatAI/gemma-3-27b-it-FP8-dynamic --served-model-name gemma3 --host 0.0.0.0 --port 9000 --gpu-memory-utilization 0.7 --tensor-parallel-size 1 --max-model-len 65536 --dtype bfloat16 --disable-log-requests
 





https://docs.vllm.ai/en/latest/deployment/docker.html#building-vllms-docker-image-from-source

<!-- 

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

https://docs.vllm.ai/en/latest/deployment/docker.html#building-for-arm64aarch64

