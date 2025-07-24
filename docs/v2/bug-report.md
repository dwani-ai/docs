Bug Report

sudo docker run -it --runtime nvidia --gpus all \
-v ~/.cache/huggingface:/root/.cache/huggingface \
-p 8000:8000 \
--ipc=host \
--name my_vllm_container \
dwani/vllm-arm64:latest

sudo docker exec -it my_vllm_container /bin/bash



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