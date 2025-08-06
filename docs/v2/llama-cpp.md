llama.cpp


sudo apt install libcurl4-openssl-dev

git clone https://github.com/ggml-org/llama.cpp.git
cd llama.cpp
git checkout 0d8831543cdc368fb248bae6f1b4aa5516684edc


cmake -B build -DGGML_CUDA=ON
cmake --build build --config Release

https://blogs.nvidia.com/blog/rtx-ai-garage-openai-oss/


https://huggingface.co/collections/ggml-org/gpt-oss-68923b60bee37414546c70bf

llama-server -hf ggml-org/gpt-oss-120b-GGUF -c 0 -fa --jinja --reasoning-format none

# Then, access http://localhost:8080

