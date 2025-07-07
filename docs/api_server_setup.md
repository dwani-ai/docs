
- dwani-api-server

git clone https://github.com/dwani-ai/dwani-api-server.git
cd dwani-api-server

python -m venv venv
source venv/bin/activate

pip install -r requirements.txt
docker build -t dwani/api-server-arm64:latest -f Dockerfile .



 python -m src.server.main --host 0.0.0.0 --port 18888
 