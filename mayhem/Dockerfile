# Build Stage
FROM rustlang/rust:nightly as builder

## Add source code to the build stage.
ADD . /src
WORKDIR /src

RUN cd mayhem/server && \
    env RUSTFLAGS="-g -Cdebug-assertions=on" \
        cargo +nightly -Z sparse-registry build --release && \
    mv target/release/server /server

# Package Stage
FROM rustlang/rust:nightly

COPY --from=builder /server /
