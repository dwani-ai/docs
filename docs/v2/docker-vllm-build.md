Docker Container for vllm


- python3.10 -m venv venv
- source venv/bin/activate
- pip install torch==2.7.1 torchaudio==2.7.1 torchvision --index-url https://download.pytorch.org/whl/cu128


https://github.com/sachinsshetty/jetson-containers/blob/master/docs/setup.


sudo /etc/docker/daemon.json

copy file contents from [daemon.json](../../files/daemon.json) 


 sudo systemctl restart docker

- git clone https://github.com/sachinsshetty/jetson-containers
- bash jetson-containers/install.sh
- jetson-containers build vllm

  - sudo docker tag vllm:r36.4-cu128-24.04-flashinfer vllm:latest


sudo docker build -t slabstech/dwani-vllm:latest -f Dockerfile .

sudo docker push slabstech/dwani-vllm:latest

sudo docker run --runtime nvidia -it --rm --network=host dwani:vllm

sudo docker run --runtime nvidia -it --rm -p 7890:8000 dwani:vllm

--

docker pull slabstech/dwani-vllm:latest
sudo docker tag slabstech/dwani-vllm:latest dwani/vllm-arm64:latest

sudo docker push dwani/vllm-arm64:latest
