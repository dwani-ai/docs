Bug Report

sudo docker run -it --runtime nvidia --gpus all \
-v ~/.cache/huggingface:/root/.cache/huggingface \
-p 8000:8000 \
--ipc=host \
--name my_vllm_container \
dwani/vllm-arm64:latest

sudo docker exec -it my_vllm_container /bin/bash


vllm serve Qwen/Qwen2.5-1.5B-Instruct


docker run --runtime nvidia --gpus all \
    -v ~/.cache/huggingface:/root/.cache/huggingface \
    -p 8000:8000 \
    --ipc=host \
    vllm/vllm-openai:latest \
    --model Qwen/Qwen2.5-1.5B-Instruct

docker run --runtime nvidia --gpus all \
    -v ~/.cache/huggingface:/root/.cache/huggingface \
    -p 8000:8000 \
    --ipc=host \
    dwani/vllm-new:latest \
    --model Qwen/Qwen2.5-1.5B-Instruct


sudo docker run --runtime nvidia --gpus all \
  -v ~/.cache/huggingface:/root/.cache/huggingface \
  -p 8000:8000 \
  --ipc=host \
  dwani/vllm-new:latest \
  python3 -m vllm.entrypoints.api_server --model Qwen/Qwen2.5-1.5B-Instruct



---


 sudo docker run --runtime nvidia --gpus all \
    -v ~/.cache/huggingface:/root/.cache/huggingface \
    -p 8000:8000 \
    --ipc=host \
    vllm/vllm-openai:latest \
    --model Qwen/Qwen2.5-1.5B-Instruct
Unable to find image 'vllm/vllm-openai:latest' locally
latest: Pulling from vllm/vllm-openai
Digest: sha256:37cd5bd18d220a0f4c70401ce1d4a0cc588fbfe03cc210579428f2c47e6eac33
Status: Downloaded newer image for vllm/vllm-openai:latest
WARNING: The requested image's platform (linux/amd64) does not match the detected host platform (linux/arm64/v8) and no specific platform was requested
exec /usr/bin/python3: exec format error


---

DOCKER_BUILDKIT=1 docker build . \
  --target vllm-openai \
  --platform "linux/arm64" \
  -t vllm/vllm-gh200-openai:latest \
  --build-arg max_jobs=66 \
  --build-arg nvcc_threads=2 \
  --build-arg torch_cuda_arch_list="9.0+PTX" \
  --build-arg vllm_fa_cmake_gpu_arches="90-real"


--



docker run --runtime nvidia --gpus all \
    -v ~/.cache/huggingface:/root/.cache/huggingface \
    --env "HUGGING_FACE_HUB_TOKEN=<secret>" \
    -p 8000:8000 \
    --ipc=host \
    vllm/vllm-openai:latest \
    --model Qwen/Qwen2.5-1.5B-Instruct


- triton
nvcr.io/nvidia/tritonserver:25.06-vllm-python-py3

- cuda
nvcr.io/nvidia/cuda:12.8.1-cudnn-devel-ubuntu22.04

- pytorch
nvcr.io/nvidia/pytorch:25.06-py3


- 

<!-- 
sudo docker pull nvcr.io/nvidia/tritonserver:25.06-vllm-python-py3


docker run --gpus all -it --rm --net=host -p 8001:8001 \
  --shm-size=1G --ulimit memlock=-1 --ulimit stack=67108864 \
  -v ${PWD}/model_repository:/model_repository \
  nvcr.io/nvidia/tritonserver:25.06-vllm-python-py3 \
  tritonserver --model-store=/model_repository



git clone https://github.com/triton-inference-server/server

cd server/docs/examples/

bash fetch_models.sh

quickstart - https://github.com/triton-inference-server/server/blob/main/docs/getting_started/quickstart.md

-->