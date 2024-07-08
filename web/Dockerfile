FROM golang:latest

WORKDIR /app

RUN apt update && apt install -y unzip wget chromium chromium-driver

# Download chromedriver for the linux64 architecture
RUN wget https://storage.googleapis.com/chrome-for-testing-public/126.0.6478.126/linux64/chromedriver-linux64.zip && \
    unzip chromedriver-linux64.zip && \
    mv chromedriver-linux64/chromedriver ./ && \
    chmod +x ./chromedriver

COPY src/ .

# Download all dependencies. Dependencies will be cached if the go.mod and go.sum files are not changed
RUN go mod download

# RUN go build -o main .
# CMD ["./main"]

CMD ["go", "run", "main.go"]