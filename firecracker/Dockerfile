#Dockerfile
from clearlinux:latest

ARG firecracker_release=0.13.0
ARG swupd_args

RUN swupd update $swupd_args
RUN swupd bundle-add rust-basic c-basic musl curl
RUN swupd bundle-add dev-utils-dev
RUN swupd bundle-add strace
RUN clrtrust generate
RUN cargo install cargo-vendor --root=/ && \
curl -LO https://github.com/firecracker-microvm/firecracker/archive/v${firecracker_release}.tar.gz && \
tar xf v${firecracker_release}.tar.gz && \
mv firecracker-${firecracker_release} firecracker && \
cd firecracker && \
cargo vendor
COPY config /firecracker/.cargo/config

ENV RUSTFLAGS "-C opt-level=3 -g -Clink-args=-Wl,-z,relro,-z,now"
WORKDIR /firecracker

CMD cargo install --root /out --path . --features vsock
