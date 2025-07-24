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


---

sudo docker run --runtime nvidia --gpus all \
  -v ~/.cache/huggingface:/root/.cache/huggingface \
  -p 8000:8000 \
  --ipc=host \
  dwani/vllm-new:latest \
  python3 -m vllm.entrypoints.api_server --model Qwen/Qwen2.5-1.5B-Instruct

==========
== CUDA ==
==========

CUDA Version 12.8.1

Container image Copyright (c) 2016-2023, NVIDIA CORPORATION & AFFILIATES. All rights reserved.

This container image and its contents are governed by the NVIDIA Deep Learning Container License.
By pulling and using the container, you accept the terms and conditions of this license:
https://developer.nvidia.com/ngc/nvidia-deep-learning-container-license

A copy of this license is made available in this container at /NGC-DL-CONTAINER-LICENSE for your convenience.

INFO 07-24 18:18:24 [importing.py:63] Triton not installed or not compatible; certain GPU-related functions will not be available.
WARNING 07-24 18:18:24 [importing.py:75] Triton is not installed. Using dummy decorators. Install it via `pip install triton` to enable kernel compilation.
INFO 07-24 18:18:26 [__init__.py:244] Automatically detected platform cuda.
Traceback (most recent call last):
  File "/usr/lib/python3.10/runpy.py", line 187, in _run_module_as_main
    mod_name, mod_spec, code = _get_module_details(mod_name, _Error)
  File "/usr/lib/python3.10/runpy.py", line 110, in _get_module_details
    __import__(pkg_name)
  File "/usr/local/lib/python3.10/dist-packages/vllm/__init__.py", line 13, in <module>
    from vllm.engine.arg_utils import AsyncEngineArgs, EngineArgs
  File "/usr/local/lib/python3.10/dist-packages/vllm/engine/arg_utils.py", line 22, in <module>
    from vllm.config import (BlockSize, CacheConfig, CacheDType, CompilationConfig,
  File "/usr/local/lib/python3.10/dist-packages/vllm/config.py", line 37, in <module>
    from vllm.model_executor.layers.quantization import (QUANTIZATION_METHODS,
  File "/usr/local/lib/python3.10/dist-packages/vllm/model_executor/__init__.py", line 4, in <module>
    from vllm.model_executor.parameter import (BasevLLMParameter,
  File "/usr/local/lib/python3.10/dist-packages/vllm/model_executor/parameter.py", line 10, in <module>
    from vllm.distributed import get_tensor_model_parallel_rank
  File "/usr/local/lib/python3.10/dist-packages/vllm/distributed/__init__.py", line 4, in <module>
    from .communication_op import *
  File "/usr/local/lib/python3.10/dist-packages/vllm/distributed/communication_op.py", line 9, in <module>
    from .parallel_state import get_tp_group
  File "/usr/local/lib/python3.10/dist-packages/vllm/distributed/parallel_state.py", line 150, in <module>
    from vllm.platforms import current_platform
  File "/usr/local/lib/python3.10/dist-packages/vllm/platforms/__init__.py", line 276, in __getattr__
    _current_platform = resolve_obj_by_qualname(
  File "/usr/local/lib/python3.10/dist-packages/vllm/utils.py", line 2258, in resolve_obj_by_qualname
    module = importlib.import_module(module_name)
  File "/usr/lib/python3.10/importlib/__init__.py", line 126, in import_module
    return _bootstrap._gcd_import(name[level:], package, level)
  File "/usr/local/lib/python3.10/dist-packages/vllm/platforms/cuda.py", line 18, in <module>
    import vllm._C  # noqa
ImportError: libtorch_cuda.so: cannot open shared object file: No such file or directory


---



pytorch image


------
 > [3/3] RUN pip install https://github.com/dwani-ai/vllm-arm64/releases/download/v0.0.1/vllm-0.9.2.dev144+g9206d0ff0.d20250618-cp310-cp310-linux_aarch64.whl:
0.420 ERROR: vllm-0.9.2.dev144+g9206d0ff0.d20250618-cp310-cp310-linux_aarch64.whl is not a supported wheel on this platform.
------
Dockerfile.pytorch:9
--------------------
   7 |     
   8 |     
   9 | >>> RUN pip install https://github.com/dwani-ai/vllm-arm64/releases/download/v0.0.1/vllm-0.9.2.dev144+g9206d0ff0.d20250618-cp310-cp310-linux_aarch64.whl
  10 |     
--------------------
ERROR: failed to build: failed to solve: process "/bin/sh -c pip install https://github.com/dwani-ai/vllm-arm64/releases/download/v0.0.1/vllm-0.9.2.dev144+g9206d0ff0.d20250618-cp310-cp310-linux_aarch64.whl" did not complete successfully: exit code: 1