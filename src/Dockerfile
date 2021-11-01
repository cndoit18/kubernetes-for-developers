FROM golang:1.16 as builder

WORKDIR /workspace
COPY go.mod go.mod
RUN go mod download

COPY . .
RUN go build -a -o server main.go

FROM debian:stretch

WORKDIR /
COPY --from=builder /workspace/server .

ENTRYPOINT ["/server"]