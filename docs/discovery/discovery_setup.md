### Discovery

- For server
```bash
sudo apt-get update
sudo apt-get install poppler-utils -y

git clone https://github.com/dwani-ai/discovery.git

cd discovery

python3.10 -m venv venv
source venv/bin/activate

pip install -r server-requirements.txt

export VLLM_IP=<vllm-server-ip>
uvicorn server.main:app --host 0.0.0.0 --port 18889

```
- For Local PC
```bash
sudo apt-get install tesseract-ocr

uvicorn server.local_main:app --host 0.0.0.0 --port 18889

```


- For Client
 
```bash
pip install -r client-requirements.txt

python ux/ux.py
```

<!-- 
- server/vlm/llama.md
    - Till line - 22
-->