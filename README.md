{
  "name": "Python 3",
  // Or use a Dockerfile or Docker Compose file. More info: https://containers.dev/guide/dockerfile
  "image": "mcr.microsoft.com/devcontainers/python:1-3.11-bullseye",
  "customizations": {
    "codespaces": {
      "openFiles": [
        "README.md",
        "run.py"
      ]
    },
    "vscode": {
      "settings": {},
      "extensions": [
        "ms-python.python",
        "ms-python.vscode-pylance"
      ]
    }
  },
  "updateContentCommand": "[ -f packages.txt ] && sudo apt update && sudo apt upgrade -y && sudo xargs apt install -y <packages.txt; [ -f requirements.txt ] && pip3 install --user -r requirements.txt; pip3 install --user streamlit; echo '✅ Packages installed and Requirements met'",
  "postAttachCommand": {
    "server": "streamlit run run.py --server.enableCORS false --server.enableXsrfProtection false"
  },
  "portsAttributes": {
    "8501": {
      "label": "Application",
      "onAutoForward": "openPreview"
    }
  },
  "forwardPorts": [
    8501
  ]
}
