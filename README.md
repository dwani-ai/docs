# deploy - dwani.ai

![dwani API](images/dwani-inference.drawio.png "Engine") 


- API Server 
    - sudo docker run  --env-file .env_api_server -p 80:80 dwani/api-server:latest
    - Create A Record in Cloudflare DNS and point to Static IP from GCP 