# deploy - dwani.ai

![dwani API](images/dwani-inference.drawio.png "Engine") 


Setup dwani.ai - Multimodal Inference API


- [vllm server](docs/vllm_setup.md) - text + images
- [docs-api-server](docs/docs_setup.md) - Documents : extraction, translaition, query
- [api-server](docs/api_server_setup.md) - Swagger setup
- [proxy-server](docs/proxy_setup_vm.md) - Load balancer

<!-- 

- API Server 
    - sudo docker run  --env-file .env_api_server -p 80:80 dwani/api-server:latest
    - Create A Record in Cloudflare DNS and point to Static IP from GCP 

-->