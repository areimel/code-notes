# OLLAMA Tools

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

## GPU Tools
Show GPU usage: `watch -n 2 nvidia-smi --id=1`
```terminal
watch -n 2 nvidia-smi
```

Show full GPU info:
```terminal
nvidia-smi -a
```

## Benchmarking

https://github.com/cloudmercato/ollama-benchmark 