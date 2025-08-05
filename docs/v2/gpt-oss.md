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

https://huggingface.co/blog/welcome-openai-gpt-oss


RoPe - https://arxiv.org/abs/2104.09864

MoE - https://arxiv.org/abs/1701.06538


GPT3- https://arxiv.org/abs/2005.14165

GPT 2 - 
https://cdn.openai.com/better-language-models/language_models_are_unsupervised_multitask_learners.pdf


https://cookbook.openai.com/articles/run-nvidia


https://developer.nvidia.com/blog/delivering-1-5-m-tps-inference-on-nvidia-gb200-nvl72-nvidia-accelerates-openai-gpt-oss-models-from-cloud-to-edge/
