# 特定のOSバージョンを指定（bookwormなど）して安定性を確保
FROM mcr.microsoft.com/vscode/devcontainers/python:3.11-bookworm

# 必須のシステムパッケージのみインストール
RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential \
    git \
    # Raspi(ARM)でもPC(x86)でも計算を高速化する汎用ライブラリ
    libatlas-base-dev \ 
    && apt-get clean && rm -rf /var/lib/apt/lists/*

# 依存ライブラリのインストール
COPY requirements.txt /tmp/pip-tmp/
RUN pip3 install --no-cache-dir -r /tmp/pip-tmp/requirements.txt \
    && rm -rf /tmp/pip-tmp