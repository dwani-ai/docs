
Translate Server

- https://github.com/dwani-ai/indic-translate-server.git
```bash
git clone https://github.com/dwani-ai/indic-translate-server.git
cd indic-translate-server

python -m venv --system-site-packages venv

source venv/bin/activate
pip install --upgrade pip setuptools wheel packaging cython

pip install torch==2.7.1 torchvision torchaudio --index-url https://download.pytorch.org/whl/cu128

#pip install -r requirements.txt

pip install -e git+https://github.com/VarunGumma/IndicTransToolkit.git@main#egg=IndicTransToolkit

pip install fastapi uvicorn  "numpy<2.0"
python src/server/translate_api.py --host 0.0.0.0 --port 7862 --device cpu
```
