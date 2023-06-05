FROM node:16-apline as builder
WORKDIR '/app'
COPY ./package.json ./
RUN npm install
COPY . .
RUN npm run build

FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
# copy results from step builder into the servers dire of the container
COPY --from=builder /app/build /user/share/nginx/html