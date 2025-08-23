gpt-oss via tensorRT-LLM


sudo docker run --rm --ipc=host -it \
  --ulimit stack=67108864 \
  --ulimit memlock=-1 \
  --gpus all \
  -p 8000:8000 \
  -e TRTLLM_ENABLE_PDL=1 \
  -e TRT_LLM_DISABLE_LOAD_WEIGHTS_IN_PARALLEL=True \
  -v ~/.cache:/root/.cache:rw \
  nvcr.io/nvidia/tensorrt-llm/release:gpt-oss-dev \
  /bin/bash

cat <<EOF > low_latency.yaml
enable_attention_dp: false
enable_mixed_sampler: true
cuda_graph_config:
    max_batch_size: 8
    enable_padding: true
moe_config:
    backend: TRITON
EOF


mpirun -n 1 --oversubscribe --allow-run-as-root \
trtllm-serve  openai/gpt-oss-20b \
  --host 0.0.0.0 \
  --port 9500 \
  --backend pytorch \
  --tp_size 1 \
  --ep_size 1 \
  --trust_remote_code \
  --extra_llm_api_options low_latency.yaml \
  --kv_cache_free_gpu_memory_fraction 0.75



curl -s -o /dev/null -w "Status: %{http_code}\n" "http://localhost:9500/health"  


curl localhost:9500/v1/chat/completions -H "Content-Type: application/json" -d '{
    "model": "openai/gpt-oss-120b",
    "messages": [
        {
            "role": "user",
            "content": "What is NVIDIAs advantage for inference?"
        }
    ],
    "max_tokens": 1024,
    "top_p": 0.9
}' -w "\n"