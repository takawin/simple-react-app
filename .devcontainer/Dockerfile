FROM ubuntu:22.04

SHELL ["/bin/bash", "-c"]

RUN apt update \
    && apt install -y git vim curl zip unzip sudo ca-certificates gnupg \
    && groupadd --gid 1000 sudogroup \
    && useradd --uid 1000 --shell /bin/bash --gid 1000 -m vscode \
    && echo %sudogroup ALL=\(ALL\) NOPASSWD: ALL > /etc/sudoers.d/sudogroup

## Node.js関係の処理
## 参考: https://github.com/nodesource/distributions
RUN mkdir -p /etc/apt/keyrings \
    && curl -fsSL https://deb.nodesource.com/gpgkey/nodesource-repo.gpg.key | gpg --dearmor -o /etc/apt/keyrings/nodesource.gpg \
    && echo "deb [signed-by=/etc/apt/keyrings/nodesource.gpg] https://deb.nodesource.com/node_21.x nodistro main" | tee /etc/apt/sources.list.d/nodesource.list \
    && apt update \
    && apt install nodejs -y
