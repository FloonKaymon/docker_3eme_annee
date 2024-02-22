# Créer un Dockerfile pour cette application en mode production

FROM rustlang/rust:nightly

RUN apt-get update -y && apt-get install -y gcc libpq-dev

COPY . /app
WORKDIR /app

RUN cargo install --path .

RUN cp /usr/local/cargo/bin/blog ./blog

RUN cargo install diesel_cli --no-default-features --features postgres