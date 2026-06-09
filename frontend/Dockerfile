FROM node:18 as build

WORKDIR /app
COPY . .
RUN npm install && npm run build

FROM nginx:alpine

# remove default config
RUN rm /etc/nginx/conf.d/default.conf

# copy custom config
COPY nginx.conf /etc/nginx/conf.d/default.conf

# copy build files
COPY --from=build /app/build /usr/share/nginx/html
