Docker Container for vllm

```bash
python3.10 -m venv venv
source venv/bin/activate
pip install torch==2.7.1 torchaudio==2.7.1 torchvision --index-url https://download.pytorch.org/whl/cu128



sudo /etc/docker/daemon.json
```
copy file contents from [daemon.json](../../files/daemon.json) 


```bash
 sudo systemctl restart 
 
 export INDEX_HOST=jetson-ai-lab.io



git clone https://github.com/sachinsshetty/jetson-containers
bash jetson-containers/install.sh

CUDA_VERSION=12.8 jetson-containers build pytorch

CUDA_VERSION=12.8 jetson-containers build vllm


jetson-containers build vllm

```
  - sudo docker tag vllm:r36.4-cu128-24.04-flashinfer vllm:latest


sudo docker build -t slabstech/dwani-vllm:latest -f Dockerfile .

sudo docker push slabstech/dwani-vllm:latest

sudo docker run --runtime nvidia -it --rm --network=host dwani:vllm

sudo docker run --runtime nvidia -it --rm -p 7890:8000 dwani:vllm

--

docker pull slabstech/dwani-vllm:latest
sudo docker tag slabstech/dwani-vllm:latest dwani/vllm-arm64:latest

sudo docker push dwani/vllm-arm64:latest


- References
  - 
  https://github.com/sachinsshetty/jetson-containers/blob/master/docs/setup.md
  