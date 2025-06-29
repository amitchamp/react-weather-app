#node block
From node:alpine3.16 as nodebuilder

WORKDIR /app

COPY ./package.json ./

RUN npm install

COPY . .

RUN npm run build

#ngnix block
FROM nginx

WORKDIR /usr/share/nginx/html

RUN rm -rf ./*

COPY --from=nodebuilder /app/build .

ENTRYPOINT [ "nginx", "-g", "daemon off;" ]
