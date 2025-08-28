## dwani-api-server

```bash
git clone https://github.com/dwani-ai/dwani-api-server.git

cd dwani-api-server

python -m venv venv
source venv/bin/activate

pip install -r requirements.txt

uvicorn src.server.main:app --host 0.0.0.0 --port 18888 

```
---
For Docker

```bash
docker build -t dwani/api-server-arm64:latest -f Dockerfile .

docker run --env-file .env.server -p 80:80 dwani/api-server-arm64:latest
```