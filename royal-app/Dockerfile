FROM golang:alpine AS builder

# Set necessary environmet variables needed for our image
ENV GO111MODULE=on \
    CGO_ENABLED=0 \
    GOOS=linux \
    GOARCH=amd64

# Move to working directory /build
WORKDIR /build

# Copy and download dependency using go mod
COPY go.mod .
COPY go.sum .
COPY . .
RUN go mod download

# Build the application
RUN go build -o main .
EXPOSE 10000
# Command to run when starting the container
CMD ["./main"]