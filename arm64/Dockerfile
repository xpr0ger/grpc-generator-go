FROM busybox:1

RUN wget https://github.com/protocolbuffers/protobuf/releases/download/v3.19.4/protoc-3.19.4-linux-aarch_64.zip -O ./protoc.zip &&\
    unzip protoc.zip -d /protoc


FROM arm64/golang:1.17-stretch

COPY --from=0 /protoc/bin/protoc /usr/local/bin/protoc
COPY --from=0 /protoc/include /usr/local/include

RUN go install google.golang.org/protobuf/cmd/protoc-gen-go@v1.27.1 && \
    go install google.golang.org/grpc/cmd/protoc-gen-go-grpc@v1.2.0 && \
    mkdir /proto

WORKDIR /proto
