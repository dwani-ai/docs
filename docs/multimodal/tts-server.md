
- ### TTS - Text to Speech 
- https://github.com/dwani-ai/tts-indic-server
```bash
git clone https://github.com/dwani-ai/tts-indic-server
cd tts-indic-server
git checkout gh-200
export HF_TOKEN='this-my-token'
python -m venv  venv
source venv/bin/activate
pip install wheel packaging

pip install -r requirements.txt

 pip uninstall torch torchaudio torchvision

pip install torch==2.7.1 torchvision torchaudio --index-url https://download.pytorch.org/whl/cu128

python src/gh200/main.py --host 0.0.0.0 --port 7864 --config config_two
```


