FROM node:15 as builder

WORKDIR /app

COPY package*.json .

RUN npm i

COPY . .

RUN npm run build

FROM nginx:latest

WORKDIR /usr/share/nginx/html

COPY --from=builder /app/build .

EXPOSE 80 

ENTRYPOINT ["nginx", "-g", "daemon off;"] 