# Set up Ollama Large Language Model

## Steps

To set up Ollama models on your MacBook Pro M1 Max, follow these steps:

1. Install Ollama:
   Download and install Ollama from the official website:

   ```
   https://ollama.com/download/mac
   ```

   After downloading, move the Ollama application to your Applications folder[1].

2. Open Terminal and run Ollama:
   Launch Terminal and enter the following command to start Ollama:

   ```
   ollama run llama3
   ```

   This will download and run the Llama 3 model. The initial download may take 10-15 minutes depending on your internet speed[2].

3. Verify Ollama is running:
   Open a web browser and go to:

   ```
   http://localhost:11434/
   ```

   If you see "Ollama is running", it's working correctly[2].

4. Set up aliases (optional):
   For quicker access, you can set up aliases in your ~/.zshrc file:

   ```
   vim ~/.zshrc
   ```

   Add these lines:

   ```
   alias ollama_stop='osascript -e "tell application \"Ollama\" to quit"'
   alias ollama_start='ollama run llama3'
   ```

   This allows you to start and stop Ollama easily[2].

5. Download additional models:
   You can download other models using commands like:

   ```
   ollama run mistral
   ollama run codellama:7b-code
   ```

6. Optimize for M1 Max:
   Ollama is designed to take advantage of Apple Silicon, including the M1 Max chip. It should automatically optimize performance for your hardware[4].

7. Choose appropriate model sizes:
   Your M1 Max MacBook Pro likely has sufficient RAM, but if you encounter performance issues, consider using smaller model variants. For example:
   ```
   ollama pull llama3-7b
   ollama run llama3-7b --prompt "Your prompt here"
   ```

Remember that the M1 Max chip should provide excellent performance for running these models locally. Ollama is optimized to use the Neural Engine and GPU cores of Apple Silicon chips, which should result in faster inference times[4].

If you encounter any issues with GPU utilization, make sure you're using the latest version of Ollama, as there have been reports of CPU-only usage in older versions[5].

### Citations:

[1] https://wandb.ai/byyoung3/ml-news/reports/How-to-Run-Mistral-7B-on-an-M1-Mac-With-Ollama--Vmlldzo2MTg4MjA0
[2] https://blog.shadabmohammad.com/run-llama3-on-your-m1-pro-macbook-08388b4b98e1?gi=7f2afa96ca87
[3] https://www.youtube.com/watch?v=KZBkqqcuo7g
[4] https://twm.me/posts/beginners-guide-running-llama3-ollama-mac/
[5] https://github.com/ollama/ollama/issues/1986
[6] https://www.reddit.com/r/LocalLLaMA/comments/1c8nq9a/mac_m1_ollama_and_llama3/
[7] https://news.ycombinator.com/item?id=37269645
[8] https://www.llama.com/docs/llama-everywhere/running-meta-llama-on-mac/

## Other Resources

- model zoo: https://huggingface.co/models?pipeline_tag=llama
- ollama models: https://ollama.com/library
