FROM node:10 As builder

WORKDIR /app

COPY . .

RUN npm install

RUN npm run build --configuration=production

FROM nginx:latest

COPY nginx/ /etc/nginx/

COPY entrypoint.sh /docker-entrypoint.d/entrypoint.sh

COPY --from=builder /app/dist/* /usr/share/nginx/html

LABEL maintainer="Florian"