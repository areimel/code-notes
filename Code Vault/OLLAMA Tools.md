# OLLAMA Tools

Test network connection
```bash
curl http://0.0.0.0:11434/api/generate -d '
{
  "model": "tinyllama",
  "prompt": "Why is the sky blue?",
  "stream": false,
  "options": {
    "num_thread": 8,
    "num_ctx": 2024
  }
}' | jq .
```
