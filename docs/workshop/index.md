## Workshop steps

- Live Website : [https://workshop.dwani.ai](https://workshop.dwani.ai)

### For Development 
- **Prerequisites**: Python 3.10
- **Steps**:
  1. **Create a virtual environment**:
  ```bash
  python3 -m venv venv
  ```
  2. **Activate the virtual environment**:
  ```bash
  source venv/bin/activate
  ```
  On Windows, use:
  ```bash
  venv\Scripts\activate
  ```
  3. **Install dependencies**:
  ```bash
  pip install -r requirements.txt
  ```
  4. **Setup Credentials**:
  ```bash
  export DWANI_API_BASE_URL=<dwnai-ip>
  export DWANI_API_KEY=<dwani_key>
  ```
  5. **Run the Program**:
  - ```bash
    python workshop_demo.py
    ```

- To Run the program
  - DWANI_API_BASE_URL and DWANI_API_KEY environment variables has to be set
    - export DWANI_API_BASE_URL=http://example.com
    - export DWANI_API_KEY='your_api_key_here'

  - Please email us to get the IP for dwani.ai - workshop inference server




<!-- 

## Video Tutorials

- dwani - How to use - dwani AI - Workshop:  20th March, 2025
[![Watch the video](https://img.youtube.com/vi/RLIhG1bt8gw/hqdefault.jpg)](https://youtu.be/f5JkJLQJFGA)

- dwani - Intoduction to Project
[![Watch the video](https://img.youtube.com/vi/kqZZZjbeNVk/hqdefault.jpg)](https://youtu.be/kqZZZjbeNVk)

-->


<!-- 
docker run -p 80:80 --env DWANI_API_KEY=<your__key> --env DWANI_API_BASE_URL="https://api.dwani.ai"  --env GPT_OSS_API_URL=11 --env GEMMA_VLLM_IP=11 dwani/workshop:latest

nohup python src/server/main.py --port 7860 > server.log 2>&1 &

docker build -t dwani/workshop:latest -f Dockerfile .
docker push dwani/workshop:latest

docker run -p 80:80 --env DWANI_API_KEY=<your_key> --env DWANI_API_BASE_URL=<your_url>  --env GPT_OSS_API_URL=<gpt_url> --env GEMMA_VLLM_IP=<gemma_ip> dwani/workshop:latest

docker run -p 80:80 --env DWANI_API_KEY=$DWANI_API_KEY --env DWANI_API_BASE_URL=$DWANI_API_BASE_URL --env GPT_OSS_API_URL=$GPT_OSS_API_URL --env GEMMA_VLLM_IP=$GEMMA_VLLM_IP  dwani/workshop:latest
34.42.91.97

pip install git+https://github.com/dwani-ai/dwani-python-sdk.git@document-sppedup-v2
-->
