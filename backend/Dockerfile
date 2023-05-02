FROM golang:alpine AS builder 

WORKDIR /src
ENV CGO_ENABLED=0
COPY go.* .
COPY src .
RUN --mount=type=cache,target=/go/pkg/mod \
    go mod download

ARG TARGETOS
ARG TARGETARCH
RUN --mount=target=. \
    --mount=type=cache,target=/go/pkg/mod \
    --mount=type=cache,target=/root/.cache/go-build \
    GOOS=${TARGETOS} GOARCH=${TARGETARCH} go build -o /out/api  ./src

FROM alpine
RUN apk update --no-cache && apk add --no-cache ca-certificates tzdata

WORKDIR /app
COPY --from=builder /out/api /app/backend

CMD ["./backend"]
