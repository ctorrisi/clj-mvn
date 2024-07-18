FROM opensuse/tumbleweed:latest

RUN zypper ref && \
    zypper install -y sudo systemd

RUN echo '%wheel ALL=(ALL) NOPASSWD:ALL' > /etc/sudoers.d/wheel && \
    chmod 440 /etc/sudoers.d/wheel

CMD ["/usr/lib/systemd/systemd --switched-root --system --deserialize=4"]

