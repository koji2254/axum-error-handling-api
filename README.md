# axum-error-handling-api

# Axum Error Handling API Boilerplate

A clean, production-ready Rust asynchronous web application boilerplate utilizing the **Axum** framework. This project demonstrates how to structure custom domain errors using enums, transform them into standard HTTP client-facing responses, and write automated integration tests for your routing layers.

## 🚀 Features

- **Asynchronous Architecture:** Driven by the `tokio` runtime and `axum` server layout.
- **Unified Error Handling:** Custom `ApiError` enum implements the `IntoResponse` trait to automatically convert errors to specific HTTP status codes and uniform JSON payloads.
- **Robust Endpoint Validation:** Out-of-the-box integration testing leveraging `tower::ServiceExt::oneshot` to simulate real HTTP requests inside test environments.

## 🛠️ Prerequisites

Ensure your system has the standard Rust toolchain installed:
- Rust (Edition 2021)
- Cargo Package Manager

Verify installation by running:
```bash
rustc --version
```

## 📦 Core Dependencies

This project relies on the following ecosystem components inside `Cargo.toml`:
*   `axum` (v0.7) - Web framework routing and layer architecture.
*   `tokio` - Multi-threaded asynchronous execution wrapper.
*   `serde_json` - JSON serialization and evaluation.
*   `tower` & `http-body-util` - Network request primitives and test helpers.

## 🏃 Getting Started

### 1. Run the Server
Launch the local daemon bound to port `3000`:
```bash
cargo run
```
*Expected console output:*
```text
Server running on http://localhost:3000
```

### 2. Live API Testing
You can interact with your application via terminal loops using `curl`:

*   **Health Check Evaluation:**
    ```bash
    curl http://localhost:3000/health
    ```
    *Response:* `{"message":"Server is running","status":"ok"}`

*   **Valid User Retrieval:**
    ```bash
    curl http://localhost:3000/users/42
    ```
    *Response:* `{"id":42,"name":"User Name"}`

*   **Custom Client Error Triggers:**
    ```bash
    curl http://localhost:3000/users/150
    ```
    *Response (404 Not Found):* `{"error":"Data not found"}`

*   **Internal Errors Mapping Validation:**
    ```bash
    curl http://localhost:3000/users
    ```
    *Response (500 Internal Server Error):* `{"error":"Internal server error: "}`

## 🧪 Testing Layout

Automated tests check both raw error transformations and functional routing integration layers. Run tests seamlessly with Cargo:

```bash
cargo test
```
