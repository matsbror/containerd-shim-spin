FROM --platform=${BUILDPLATFORM} rust:1.73 AS build
WORKDIR /opt/build
COPY . .
RUN rustup target add wasm32-wasi && cargo build --target wasm32-wasi --release

FROM scratch
COPY --from=build /opt/build/target/wasm32-wasi/release/mqtt_message_logger.wasm ./target/wasm32-wasi/release/mqtt_message_logger.wasm
COPY --from=build /opt/build/spin.toml .