# Créer un Dockerfile pour cette application en mode production

FROM rustlang/rust:nightly

RUN apt-get update -y && apt-get install -y gcc libpq-dev netcat

ENV DATABASE_URL=postgres://blog:blog@blog_db:5432/blog
ENV ROCKET_ADDRESS=0.0.0.0

COPY . /app
WORKDIR /app

RUN cargo install --path .

RUN cp /usr/local/cargo/bin/blog ./blog

RUN cargo install diesel_cli --no-default-features --features postgres