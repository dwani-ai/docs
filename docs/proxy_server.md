Proxy Server

docker build -t dwani/proxy-server:latest -f Dockerfile .


docker push dwani/proxy-server:latest

docker run --env-file .env -p 80:80 dwani/proxy-server:latest