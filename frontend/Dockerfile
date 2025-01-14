FROM node:18-slim AS build

WORKDIR /app

COPY . .

RUN npm install && npm run build

FROM nginx:1.22.1

COPY --from=build /app/build /usr/share/nginx/html

EXPOSE 3000

CMD ["nginx", "-g", "daemon off;"]
