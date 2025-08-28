llama.cpp for for Discovery

- Setup llama.cpp 
```bash
sudo apt install libcurl4-openssl-dev

git clone https://github.com/ggml-org/llama.cpp.git
cd llama.cpp
```
    - With NVIDIA GPU and CUDA Toolkit
    ```bash
    cmake -B build -DGGML_CUDA=ON
    ```
    - for CPU 
    ```bash
    cmake -B build
    ```
- Create Executable
```bash
cmake --build build --config Release -j4
```

- To run Gemma-3-4b-IT
```bash
./build/bin/llama-server -hf ggml-org/gemma-3-4b-it-GGUF --host 0.0.0.0 --port 9000 --n-gpu-layers 99 --ctx-size 8192 --alias gemma3

```

- To - OpenAI - gpt-oss-20b
    - For Laptop / PC -  gpt-oss-20b
```bash
./build/bin/llama-server -hf ggml-org/gpt-oss-20b-GGUF -c 0 -fa --jinja --reasoning-format none --port 9500
```
    - For H100/H200 - gpt-oss-120b
```bash
./build/bin/llama-server -hf ggml-org/gpt-oss-120b-GGUF -c 0 -fa --jinja --reasoning-format none --port 9500
```

- Then, access http://localhost:8080


- Reference 
    - https://blogs.nvidia.com/blog/rtx-ai-garage-openai-oss/
    - HF model repo - https://huggingface.co/collections/ggml-org/gpt-oss-68923b60bee37414546c70bf
