### docs-indic-server


```bash
git clone https://github.com/dwani-ai/docs-indic-server.git
cd docs-indic-server

python -m venv --system-site-packages venv

source venv/bin/activate

pip install -r requirements.txt
pip install "numpy<2.0"

python src/server/docs_api.py  --host 0.0.0.0 --port 7861
```

- Dependencies
  - decord
```bash
cd
mkdir external
cd external
git clone --recursive https://github.com/dmlc/decord

cd decord

mkdir build && cd build

export CUDA_TOOLKIT_ROOT_DIR=/usr/local/cuda
export CUDACXX=/usr/local/cuda/bin/nvcc

nvcc --version

cmake .. -DUSE_CUDA=1 -DCMAKE_BUILD_TYPE=Release -DFFMPEG_DIR=/usr

cmake .. -DUSE_CUDA=1 -DCMAKE_BUILD_TYPE=Release

make

cd ../python
python3 setup.py install --user
pip install "numpy<2.0"

```
  - olmocr
```bash
cd ../../
git clone  https://github.com/allenai/olmocr.git

cd olmocr

pip install --upgrade pip setuptools wheel packaging

 // copy ppyproject.toml
pip install -e .
cd ../../dwani_org/gh-200-docs-indic-server/
pip install "numpy<2.0"
```
  - ffmpeg
  ```bash
  sudo apt update
  sudo apt install ffmpeg
  ffmpeg -version

  sudo apt update
  sudo apt install cmake ffmpeg build-essential python3-dev

  sudo apt install pkg-config libavcodec-dev libavformat-dev libavutil-dev libswscale-dev libswresample-dev  libavfilter-dev 

  sudo apt-get install poppler-utils
  ```
<!-- 
find /usr/lib* -name libavformat.so



sudo ln -s /usr/lib/aarch64-linux-gnu/libavformat.so /usr/lib/libavformat.so
sudo ln -s /usr/lib/aarch64-linux-gnu/libavcodec.so /usr/lib/libavcodec.so
sudo ln -s /usr/lib/aarch64-linux-gnu/libavutil.so /usr/lib/libavutil.so
sudo ln -s /usr/lib/aarch64-linux-gnu/libavfilter.so /usr/lib/libavfilter.so
sudo ln -sf /usr/lib/aarch64-linux-gnu/libavdevice.so.58 /usr/lib/libavdevice.so

sudo ln -s /usr/lib/aarch64-linux-gnu/libswresample.so  /usr/lib/libswresample.so

sudo ldconfig
# Add other FFmpeg libs as 
cmake .. -DUSE_CUDA=1 -DCMAKE_BUILD_TYPE=Release -DFFMPEG_LIB_DIR=/usr/lib/aarch64-linux-gnu -DFFMPEG_INCLUDE_DIR=/usr/include

-->


<!-- 
in olmocr :  pyproject.toml - remove sql-kernem and sglang
set python version to 3.10


python src/server/docs_api.py  --host 0.0.0.0 --port 7861

-->