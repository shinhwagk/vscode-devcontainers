FROM golang:1

ARG USERNAME=vscode
ARG USER_UID=1000
ARG USER_GID=$USER_UID

RUN groupadd --gid $USER_GID $USERNAME \
    && useradd --uid $USER_UID --gid $USER_GID -m $USERNAME

RUN go env -w GOPROXY=https://mirrors.aliyun.com/goproxy

RUN GOPATH=/tmp/gotools GO111MODULE=on go get -v golang.org/x/tools/gopls
RUN GOPATH=/tmp/gotools GO111MODULE=off go get -v github.com/uudashr/gopkgs/v2/cmd/gopkgs

RUN go env -w GO111MODULE=on