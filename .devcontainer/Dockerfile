FROM rust:1.78.0

WORKDIR /app

RUN export DEBIAN_FRONTEND=noninteractive && \
    apt-get update && \
    apt-get install -y --no-install-recommends \
        git \
        vim \
        gnupg \
        openssh-client \
        bash-completion \
        sudo && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* && \
    groupadd -g 1000 dev && \
    useradd -l -u 1000 -g dev dev -m -s /bin/bash && \
    echo "dev ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/dev && \
    chmod 0440 /etc/sudoers.d/dev && \
    chown -R dev:dev /app && \
    rustup component add rustfmt clippy && \
    git config --global safe.directory '*'

USER dev
