# CrabThread

CrabThread is a multi-threaded web server built with Rust, demonstrating concurrent request handling using a thread pool. It's an implementation of the final project from the official Rust book.

## About

This project showcases advanced Rust programming concepts:

- Multi-threaded programming with thread pools
- TCP server implementation
- HTTP request parsing
- Graceful shutdown handling
- Message passing between threads using channels
- Shared state management with `Arc` and `Mutex`

## Features

- **Thread Pool**: Efficiently manages a pool of worker threads to handle concurrent requests
- **HTTP Support**: Handles basic HTTP GET requests
- **Graceful Shutdown**: Properly cleans up resources when the server stops
- **Configurable**: Easy to modify port and thread pool size

## Getting Started

### Prerequisites

- Rust (latest stable version recommended)
- Cargo

### Installation

1. Clone the repository:

```bash
git clone https://github.com/devwraithe/crab-thread.git
cd crab-thread
```

2. Build the project:

```bash
cargo build --release
```

3. Run the server:

```bash
cargo run --release
```

The server will start listening on `127.0.0.1:7878`.

## Usage

### Starting the Server

```bash
cargo run --release
```

### Testing the Server

Open your browser and navigate to:

```
http://127.0.0.1:7878
```

Or use curl:

```bash
curl http://127.0.0.1:7878
```

### Configuration

You can modify the server configuration in `src/main.rs`:

- **Port**: Change the bind address (default: `127.0.0.1:7878`)
- **Thread Pool Size**: Adjust the number of worker threads (default: 4)

## Project Structure

```
crab-thread/
├── src/
│   ├── main.rs          # Server setup and request handling
│   └── lib.rs           # Thread pool implementation
├── static/              # HTML files served by the server
├── Cargo.toml
└── README.md
```

## How It Works

1. The server creates a thread pool with a fixed number of worker threads
2. When a request arrives, it's assigned to an available worker thread
3. The worker thread processes the request and sends the response
4. The thread returns to the pool, ready to handle the next request

This architecture allows the server to handle multiple concurrent connections efficiently without spawning a new thread for each request.

## Example Response

The server serves static HTML files from the project directory and can simulate slow requests to demonstrate concurrent handling.
