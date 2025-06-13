
FROM node:20-alpine AS base

WORKDIR /app

COPY package*.json .

RUN npm install

COPY . .

## build project

FROM base AS build

RUN npm run build

## developement mode

FROM base as dev

CMD [ "npm", "run", "dev" ]

## production mode

FROM nginx:alpine AS prod

COPY --from=build /app/dist /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]