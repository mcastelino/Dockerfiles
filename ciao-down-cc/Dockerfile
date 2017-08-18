#
# Clear Linux VM Sandbox for Clear Containers
#
#
# Running this container
#
# sudo docker run -it -e http_proxy=$http_proxy -e https_proxy=$https_proxy --privileged --runtime=runc mcastelino/ciao-down-cc
#
# The container needs to run as privileged in order to launch the ciao-down virtual machine
# that will host clear containers
#
# To try clear-containers
#
# 1. Setup the VM sandbox
#    ciao-down create clearcontainers
# 
# 2. Connect to the VM
#    ciao-down connect
#
# 3. Run clear containers with the virtual machine
#

FROM golang:1.8

RUN apt update

RUN apt install -y xorriso

RUN apt install -y qemu

RUN go get github.com/01org/ciao/testutil/ciao-down

ENV USER root
