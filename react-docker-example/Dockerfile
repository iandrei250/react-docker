FROM node:20-alpine as build

WORKDIR /react-docker-example/

COPY public/ /react-docker-example/public
COPY src/ /react-docker-example/src
COPY package.json /react-docker-example/

RUN npm install

RUN npm run build

FROM nginx:alpine

COPY --from=build /react-docker-example/build /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]