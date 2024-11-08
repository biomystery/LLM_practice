# Add models to RagFlow

## Steps by steps

1. Verify model availability:
   Run `ollama list` to ensure the `mxbai-embed-large:latest` model is actually available in your Ollama installation.

2. Check model name:
   Make sure the model name in RAGFlow exactly matches what's listed in Ollama. It should be `mxbai-embed-large:latest` (including the `:latest` tag).

3. Test embedding directly:
   Try to generate embeddings directly using Ollama's API:

   ```bash
   curl -X POST http://localhost:11434/api/embeddings -d '{
     "model": "mxbai-embed-large:latest",
     "prompt": "Test embedding"
   }'
   ```

   If this fails, the issue is with Ollama's embedding functionality.

4. Check Ollama logs:
   Look for any error messages in Ollama's logs that might indicate why it's not accepting embedding requests.

5. Restart Ollama:
   Try stopping and restarting the Ollama service:

   ```bash
   ollama stop
   ollama start
   ```

6. Network configuration:
   Ensure RAGFlow is using the correct address to reach Ollama. If they're running in different environments (e.g., Docker containers), you might need to use `http://host.docker.internal:11434` instead of `localhost`.

7. Firewall issues:
   Check if there's a firewall blocking connections specifically for embedding requests.

8. IPv4 vs IPv6:
   Based on the error message, it seems RAGFlow might be trying to connect via IPv6. Try forcing IPv4 by using `http://127.0.0.1:11434` instead of `localhost`.

9. Update RAGFlow configuration:
   Double-check the Ollama configuration in RAGFlow's settings. Make sure the base URL and model name are correct.

10. Version compatibility:
    Ensure you're using compatible versions of RAGFlow and Ollama.

If you've gone through these steps and are still encountering the error, you may need to:

- Check RAGFlow's logs for more detailed error messages
- Consider reinstalling Ollama if you suspect it's not functioning correctly
- Consult RAGFlow's documentation or support channels for specific configuration requirements

Remember to restart both RAGFlow and Ollama after making any configuration changes to ensure they take effect.

## Citations:

[1] https://github.com/weaviate/Verba/issues/252
[2] https://stackoverflow.com/questions/2333400/what-can-be-the-reasons-of-connection-refused-errors
[3] https://github.com/open-webui/pipelines/issues/255
[4] https://www.greengeeks.com/tutorials/err_connection_refused/
[5] https://huggingface.co/mixedbread-ai/mxbai-embed-large-v1
[6] https://www.keycdn.com/support/err-connection-refused
[7] https://www.dreamhost.com/blog/how-to-fix-connection-refused-error/
[8] https://ragflow.io/docs/dev/faq
