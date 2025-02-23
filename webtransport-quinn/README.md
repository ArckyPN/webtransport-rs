[![Documentation](https://docs.rs/webtransport-quinn/badge.svg)](https://docs.rs/webtransport-quinn/)
[![Crates.io](https://img.shields.io/crates/v/webtransport-quinn.svg)](https://crates.io/crates/webtransport-quinn)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE-MIT)

# webtransport-quinn

## Example

See the example [server](examples/echo-server.rs) and [client](examples/echo-client.rs).

QUIC requires TLS, which makes the initial setup a bit more involved.

-   Generate a certificate: `./cert/generate`
-   Run the Rust server: `cargo run --example echo-server --tls-cert cert/localhost.crt --tls-key cert/localhost.key`
-   Run the Rust client: `cargo run --example echo-client --tls-cert cert/localhost.crt`
-   Run a Web client: `cd web; npm install; npx parcel serve client.html --open`

## Limitations

This library doesn't support pooling HTTP/3 or multiple WebTransport sessions.
It's means to be analogous to the QUIC API.

-   If you want to support HTTP/3 on the same host/port, you should use another crate (ex. `h3-webtransport`).
-   If you want to support multiple WebTransport sessions over the same QUIC connection... you should just dial a new QUIC connection instead.
