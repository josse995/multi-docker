FROM node:alpine
WORKDIR "/app"
COPY ./package*.json ./
RUN npm install
RUN mkdir -p /app/node_modules/.cache && chmod -R 777 /app/node_modules/.cache
COPY . .
RUN yarn build

FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=0 /app/build /usr/share/nginx/html
