FROM node:latest
EXPOSE 3000
WORKDIR /makemewatch
COPY . .
RUN npm install && npm run build
CMD node dist/main.js