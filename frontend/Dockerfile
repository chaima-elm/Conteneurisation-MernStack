FROM node:12.22.7-alpine AS build
WORKDIR /src
COPY package.json .
RUN npm install
COPY . /src
RUN npm run build

FROM nginx:1.23.2-alpine as production
COPY --from=build /src/build /usr/share/nginx/html
COPY --from=build /src/nginx/nginx.conf /etc/nginx/conf.d/default.conf
EXPOSE 80
