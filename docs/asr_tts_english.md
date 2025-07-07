
ASR - English

curl --silent --remote-name https://raw.githubusercontent.com/speaches-ai/speaches/master/compose.yaml
curl --silent --remote-name https://raw.githubusercontent.com/speaches-ai/speaches/master/compose.cuda.yaml
export COMPOSE_FILE=compose.cuda.yaml

sudo docker compose -f compose.cuda.yaml up -d


curl -X 'POST' \
  'http://localhost:8000/v1/models/Systran/faster-whisper-small' \
  -H 'accept: application/json' \
  -d ''


  curl -X 'POST' \
  'http://localhost:8000/v1/models/speaches-ai/Kokoro-82M-v1.0-ONNX' \
  -H 'accept: application/json' \
  -d ''



