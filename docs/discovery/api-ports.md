# Run your app normally (no sudo needed)
uvicorn src.server.main:app --host 0.0.0.0 --port 8000

# In another terminal (as root), set up redirection (persists until reboot)
sudo iptables -t nat -A PREROUTING -p tcp --dport 80 -j REDIRECT --to-port 8000
sudo iptables -t nat -A OUTPUT -p tcp -o lo --dport 80 -j REDIRECT --to-port 8000  # Optional: for localhost access


nohup python src/multi-lingual/asr_api.py --port 7863 --host 0.0.0.0 --device cuda > asr.log 2>&1 &

nohup uvicorn src.server.main:app --host 0.0.0.0 --port 18888 > api-server.log 2>&1 &