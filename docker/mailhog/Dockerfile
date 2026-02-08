FROM golang:bookworm

# Install necessary dependencies
RUN apt update && apt install -y  \
    golang-go \
    wget \
    dos2unix \
    && apt clean

ENV GOBIN=/usr/local/bin
ENV PATH="/root/go/bin:$PATH"

# Install MailHog using Go
RUN go install github.com/mailhog/MailHog@latest


# Copy the commands directory into the container
COPY commands/setup_mailhog_auth.sh /commands/setup_mailhog_auth.sh

# Ensure all scripts in the commands directory have Unix-style line endings and are executable
RUN dos2unix /commands/setup_mailhog_auth.sh && chmod +x /commands/setup_mailhog_auth.sh
