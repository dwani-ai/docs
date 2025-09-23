Setup Cloudflare

- Steps

  - Install cloudflared
    - https://developers.cloudflare.com/cloudflare-one/connections/connect-networks/downloads/

    - Ubuntu/linux
      - 
```bash
      wget https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-amd64.deb
      sudo apt install -f ./cloudflared-linux-amd64.deb

      cloudflared login

```

- Go to ZeroTrust in Cloudflare website
  - Click Networks
    - Click Tunnels
      - Create a tunnel
        - Name your runnel
          - Insall and run connector step
            - sudo cloudflared service install <TOEKN>
          - Click Neext
            - Publish Application PAge
              - Hostname ? 
                - Service - http://localhost:18888

    - via Docker ?
      - https://hub.docker.com/r/cloudflare/cloudflared
