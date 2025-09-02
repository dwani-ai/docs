Setup vllm for arm64

- Install - python3.12 - [python_3_12.md](python_3_12.md)
- Create vllm wheel - [vllm-setup.md](vllm-setup.md)
- Create vllm-docker - [vllm_docker_build.md](vllm_docker_build.md)


- Open Items
    - flash-infer
    - xformers


<!-- 
  - Reduce vLLM wheel size build 
    - < 100 MB for pypi  
        - Issue 
            - https://docs.pypi.org/project-management/storage-limits/
        - Temporary Fix : uploaded to GitHub Releass
    - < 400 MB for docker 
        - Issue
            - https://github.com/vllm-project/vllm/blob/main/.buildkite/check-wheel-size.py
        - Temporary Fix : build-arg VLLM_MAX_SIZE_MB=1000 


 -->