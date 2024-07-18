
FROM opensuse/tumbleweed:latest

RUN zypper ref && \
    zypper install -y sudo systemd openssh chrony ModemManager NetworkManager audit irqbalance polkit postfix cronie dbus

RUN echo '%wheel ALL=(ALL) NOPASSWD:ALL' > /etc/sudoers.d/wheel && \
    chmod 440 /etc/sudoers.d/wheel

RUN systemctl enable sshd chronyd ModemManager NetworkManager auditd irqbalance polkit postfix cronie dbus systemd-journald systemd-logind systemd-udevd

CMD ["/usr/lib/systemd/systemd --switched-root --system --deserialize=4"]

ENTRYPOINT ["/bin/bash", "-c", "systemctl start sshd chronyd ModemManager NetworkManager auditd irqbalance polkit postfix cronie dbus systemd-journald systemd-logind systemd-udevd && exec /usr/lib/systemd/systemd --switched-root --system --deserialize=4"]

