### BASE ###
FROM alpine:3.9 as base
ARG ARCH
RUN apk -U add \
    bash \
    bash-completion \
    blkid \
    busybox-initscripts \
    ca-certificates \
    connman \
    conntrack-tools \
    coreutils \
    curl \
    dbus \
    dosfstools \
    e2fsprogs \
    e2fsprogs-extra \
    findutils \
    grub-efi \
    haveged \
    iproute2 \
    iptables \
    jq \
    kbd-bkeymaps \
    logrotate \
    nfs-utils \
    open-iscsi \
    openrc \
    openssh-client \
    openssh-server \
    parted \
    procps \
    rsync \
    strace \
    sudo \
    tar \
    util-linux \
    vim \
    xz \
    tcpdump \
    qemu-guest-agent
RUN if [ "$ARCH" == "amd64" ]; then \
        apk add open-vm-tools grub-bios \
    ;fi
RUN cp /etc/apk/repositories /etc/apk/repositories.orig && \
    echo 'http://dl-3.alpinelinux.org/alpine/edge/testing' >> /etc/apk/repositories && \
    apk -U add efibootmgr && \
    mv /etc/apk/repositories.orig /etc/apk/repositories && \
    apk update
RUN curl -o /usr/sbin/mdata-get https://raw.githubusercontent.com/joyent/smartos-vmtools/master/src/linux/lib/smartdc/mdata-get && \
    wget -qO /usr/sbin/yq https://github.com/mikefarah/yq/releases/download/2.4.0/yq_linux_amd64 && \
    chmod +x /usr/sbin/mdata-get /usr/sbin/yq
