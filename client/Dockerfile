#Base OS
FROM node:16.13.2-alpine as builder
#New path for the container
WORKDIR /app
#Copy json file with scripts
COPY ./package.json ./
#First command to start with the container
RUN npm install
#bundly the app
COPY . .
#after pakages have been installed run this
RUN npm run build

# diffrent phase (production with Nginx)
FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html