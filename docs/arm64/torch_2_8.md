torch 2.8 for arm64


```bash
curl -LsSf https://astral.sh/uv/install.sh | INSTALLER_DOWNLOAD_URL=https://wheelnext.astral.sh sh
```
```bash
uv venv venv --python 3.12
source venv/bin/activate

uv pip install torch torchvision

```
