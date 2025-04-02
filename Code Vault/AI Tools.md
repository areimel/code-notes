# AI Tools

## Server Connections
Test network connection
```bash
curl http://0.0.0.0:11434/api/generate -d '
{
  "model": "llama3.2",
  "prompt": "Why is the sky blue?",
  "stream": false,
  "options": {
    "num_thread": 8,
    "num_ctx": 2024
  }
}' | jq .
```

## Monitoring Tools
Show GPU usage: `watch -n 2 nvidia-smi --id=1`
```wsl
watch -n 2 nvidia-smi
```

Show full GPU info:
```terminal
nvidia-smi -a
```

Bottom (Xtop alternative)
```terminal
# Install
WINDOWS: choco install bottom
LINUX: curl -LO https://github.com/ClementTsang/bottom/releases/download/0.10.2/bottom_0.10.2-1_amd64.deb
sudo dpkg -i bottom_0.10.2-1_amd64.deb
---
RUN: btm
```
## Benchmarking

https://github.com/cloudmercato/ollama-benchmark 

