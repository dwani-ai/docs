GPT OSS

https://blog.vllm.ai/2025/08/05/gpt-oss.html


https://docs.vllm.ai/projects/recipes/en/latest/OpenAI/GPT-OSS.html



docker run --gpus all \
    -p 8000:8000 \
    --ipc=host \
    vllm/vllm-openai:gptoss \
    --model openai/gpt-oss-20b

uv pip install --pre vllm==0.10.1+gptoss \
    --extra-index-url https://wheels.vllm.ai/gpt-oss/ \
    --extra-index-url https://download.pytorch.org/whl/nightly/cu128 \
    --index-strategy unsafe-best-match

vllm serve openai/gpt-oss-120b

