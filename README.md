# Face Landmark WASM

## Local Development

To run locally:

```bash
python serve.py
```

This will start a server at http://localhost:8000 with the required WASM headers.

## Deployment to Cloudflare Pages

This project is configured for Cloudflare Pages deployment:

1. Connect your GitHub repository to Cloudflare Pages
2. Use the following build settings:
   - Build command: (leave empty)
   - Build output directory: .
   - No framework preset needed

The necessary headers for WASM threading support are configured in the `_headers` file. 