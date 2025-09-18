# Build stage
FROM golang:1.21-alpine AS builder

WORKDIR /app

# Copy the Go source code
COPY app.go .

# Build the Go binary (statically linked)
RUN go build -o helloworld app.go

# Final stage: distroless image
FROM gcr.io/distroless/static-debian12:nonroot

WORKDIR /app

# Copy the statically built binary from the builder
COPY --from=builder /app/helloworld .

# Run the binary
ENTRYPOINT ["/app/helloworld"]