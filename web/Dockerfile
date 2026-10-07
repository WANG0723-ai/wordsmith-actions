FROM golang:1 AS build
WORKDIR /app
COPY dispatcher.go .
RUN --mount=type=cache,target=/root/.cache/go-build CGO_ENABLED=0 go build -ldflags="-s -w" -o dispatcher dispatcher.go

FROM scratch
WORKDIR /app
COPY --from=build /app/dispatcher ./dispatcher
COPY static ./static
CMD ["./dispatcher"]
