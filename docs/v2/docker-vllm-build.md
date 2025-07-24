Container for vllm

git clone git@github.com:sachinsshetty/jetson-containers.git

https://github.com/sachinsshetty/jetson-containers/tree/master/packages/llm/vllm


- build : vllm image
- git clone https://github.com/dusty-nv/jetson-containers
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
