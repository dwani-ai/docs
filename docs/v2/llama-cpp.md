llama.cpp for gpt-oss models from OpenAI


- sudo apt install libcurl4-openssl-dev

- git clone https://github.com/ggml-org/llama.cpp.git
- cd llama.cpp
- git checkout 0d8831543cdc368fb248bae6f1b4aa5516684edc

- With NVIDIA GPU and CUDA Toolkit
    - cmake -B build -DGGML_CUDA=ON
- for CPU 
    - cmake -B build

- cmake --build build --config Release

- For Laptop / PC -  gpt-oss-20b

    - ./build/bin/llama-server -hf ggml-org/gpt-oss-20b-GGUF -c 0 -fa --jinja --reasoning-format none


- For H100/H200 - gpt-oss-120b

    ./build/bin/llama-server -hf ggml-org/gpt-oss-120b-GGUF -c 0 -fa --jinja --reasoning-format none


- Then, access http://localhost:8080


- Reference 
  - https://blogs.nvidia.com/blog/rtx-ai-garage-openai-oss/
  - HF model repo - https://huggingface.co/collections/ggml-org/gpt-oss-68923b60bee37414546c70bf
