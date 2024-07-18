FROM opensuse/tumbleweed:latest

RUN zypper ref
RUN zypper install -y systemd sudo openssh chrony curl aaa_base bash coreutils dbus-1 glibc util-linux ModemManager NetworkManager audit irqbalance polkit cronie

RUN echo '%wheel ALL=(ALL) NOPASSWD:ALL' > /etc/sudoers.d/wheel && \
    chmod 440 /etc/sudoers.d/wheel

RUN systemctl enable sshd chronyd ModemManager NetworkManager auditd irqbalance polkit cron dbus systemd-journald systemd-logind

ENTRYPOINT ["/usr/lib/systemd/systemd"]

CMD ["--switched-root", "--system", "--deserialize=44", "--system"]

