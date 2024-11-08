# Ragflow Step by Step

To set up RAGFlow on a MacBook M1, you'll need to follow these steps:

## Prerequisites

Before starting, ensure you have:

- At least 16GB of RAM
- At least 50GB of free disk space
- Docker (version 24.0.0 or higher) and Docker Compose (version 2.26.1 or higher) installed

## Installation Process

1. **Clone the RAGFlow repository**

First, clone the RAGFlow repository from GitHub:

```bash
git clone https://github.com/infiniflow/ragflow.git
cd ragflow/docker
```

2. **Adjust system settings**

For MacOS, you need to increase the maximum number of memory map areas:

- Create a new file named `com.user.vmmaxmap.plist` in `/Library/LaunchDaemons/`
- Add the following content to the file:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
  <key>Label</key>
  <string>com.user.vmmaxmap</string>
  <key>ProgramArguments</key>
  <array>
    <string>/usr/sbin/sysctl</string>
    <string>-w</string>
    <string>vm.max_map_count=262144</string>
  </array>
  <key>RunAtLoad</key>
  <true/>
</dict>
</plist>
```

- Load the new daemon:

```bash
sudo launchctl load /Library/LaunchDaemons/com.user.vmmaxmap.plist
```

3. **Build and start the Docker containers**

For M1 Macs, you need to use a specific Dockerfile:

```bash
docker compose -f docker-compose.yml up -d
```

This command will download the necessary Docker images and start the RAGFlow services.

4. **Verify the installation**

Once the containers are up and running, you can check their status:

```bash
docker compose ps
```

All containers should show as "healthy" or "running".

5. **Access the RAGFlow interface**

Open a web browser and navigate to `http://localhost`. You should see the RAGFlow login page.

## Troubleshooting

If you encounter any issues during the installation:

- Ensure you're using the ARM-specific Dockerfile for M1 Macs[1].
- If you face package conflicts, you may need to manually install missing Python modules within the container[1].
- In case of persistent errors, try building the image without using cache and then manually installing any missing modules inside the container[1].

Remember that RAGFlow is a large application, and the initial setup may take some time, especially when downloading and building the Docker images.

## on docker img

```bash
code /ragflow/deepdoc/parser/utils.py
# change line 13 get_txt to get_text
```

## Citations:

[1] https://github.com/infiniflow/ragflow/issues/1164
[2] https://www.youtube.com/watch?v=DUqsYm_rYcA
[3] https://www.youtube.com/watch?v=Aq5TXg8H-7o
[4] https://ragflow.io/docs/dev/
[5] https://www.jeremymorgan.com/blog/generative-ai/how-to-llm-local-mac-m1/
[6] https://www.youtube.com/watch?v=bp2eev21Qfo
[7] https://stackoverflow.com/questions/66662820/m1-docker-preview-and-keycloak-images-platform-linux-amd64-does-not-match-th
[8] https://discussions.apple.com/thread/252056958
