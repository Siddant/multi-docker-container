FROM node:alpine as builder
WORKDIR '/app'
COPY package*.json ./
RUN yarn 
COPY ./ ./
RUN yarn build
# the from symbloises the start of the new step
# a single block onyl has 1 from stage
FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html
