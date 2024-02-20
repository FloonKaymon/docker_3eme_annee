FROM node:latest
ENV API_BASE_URL=http://server:3000
WORKDIR /makemewatch
COPY . .
RUN npm install && npm run build

# https://kit.svelte.dev/docs/adapter-node
CMD node build