## dwani.ai - Desktop

Use dwani.ai on your PC as offline-application

- Download the APP

- [Linux](https://github.com/dwani-ai/dwani-desktop/releases/download/v0.0.2/dwani-desktop-0.0.2.AppImage)

- [Windows](https://github.com/dwani-ai/dwani-desktop/releases/download/v0.0.2/dwani-desktop.Setup.0.0.2.exe)


- Build the Application
```bash
cd frontend
npx electron-builder --win --linux
```


- Run Application
  - linux
```bash
./dwani-desktop-0.0.1.AppImage
```

---

./build/bin/llama-server -hf ggml-org/gemma-3-4b-it-GGUF --host 0.0.0.0 --port 18888 --n-gpu-layers 99 --ctx-size 8192 --alias gemma3


run discovery server at 18889 

sudo apt-get update
sudo apt-get install poppler-utils -y

git clone https://github.com/dwani-ai/discovery.git

cd discovery

python3.10 -m venv venv
source venv/bin/activate

pip install -r server-requirements.txt

export VLLM_IP="0.0.0.0"
uvicorn server.main:app --host 0.0.0.0 --port 18889
--


