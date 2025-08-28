Proxy Server

```bash
git clone https://github.com/dwani-ai/proxy-server.git
cd proxy-server
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt

python src/server/main.py
```

For Load balancer 

```bash
git clone https://github.com/dwani-ai/proxy-server.git
cd proxy-server
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt

python src/server/load_balancer.py

```