FROM opensuse/tumbleweed:latest

RUN zypper ref
RUN zypper install -y sudo iptables systemd openssh chrony curl aaa_base bash coreutils dbus-1 glibc util-linux ModemManager NetworkManager audit irqbalance polkit postfix cronie

RUN echo '%wheel ALL=(ALL) NOPASSWD:ALL' > /etc/sudoers.d/wheel && \
    chmod 440 /etc/sudoers.d/wheel

RUN systemctl enable sshd chronyd ModemManager NetworkManager auditd irqbalance polkit postfix cron dbus systemd-journald systemd-logind

CMD ["/usr/lib/systemd/systemd --switched-root --system --deserialize=4"]

ENTRYPOINT ["/usr/lib/systemd/systemd --switched-root --system --deserialize=4"]

