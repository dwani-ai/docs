
- ### ASR - Automatic Speech Recognition / Speech to Text
    - https://github.com/dwani-ai/asr-indic-server.git
```bash
git clone https://github.com/dwani-ai/asr-indic-server.git
cd asr-indic-server
    
python -m venv --system-site-packages venv
source venv/bin/activate

pip install -r requirements.txt


python src/multilingual/asr_api.py --host 0.0.0.0 --port 7863 --device cuda

```



