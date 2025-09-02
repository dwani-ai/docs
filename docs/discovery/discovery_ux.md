Discovery UX

- With Docker

```bash
export VLLM_IP="0.0.0.0"

docker run -p 80:8000 --env VLLM_IP=$VLLM_IP dwani/discovery_ux:latest
```

- With python
```bash
git clone https://github.com/dwani-ai/discovery.git

cd discovery

python3.10 -m venv venv
source venv/bin/activate
pip install client-requirements.txt
python ux/ux.py
```