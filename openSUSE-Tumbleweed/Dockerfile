FROM opensuse/tumbleweed:latest

RUN zypper ref
RUN zypper install -y kernel-default kernel-firmware module-init-tools sudo openssh chrony curl aaa_base bash coreutils glibc ModemManager NetworkManager polkit cronie python3 irqbalance unzip

RUN echo '%wheel ALL=(ALL) NOPASSWD:ALL' > /etc/sudoers.d/wheel && \
    chmod 440 /etc/sudoers.d/wheel

RUN systemctl enable sshd chronyd ModemManager NetworkManager polkit cron dbus systemd-journald systemd-logind irqbalance

ENTRYPOINT ["/usr/lib/systemd/systemd"]

CMD ["--system"]

