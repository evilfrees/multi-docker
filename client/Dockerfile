FROM node:14.14.0-alpine
WORKDIR './app'
COPY package.json .
RUN npm install
COPY . . 
RUN npm run build

# /app/build <-- all the stuff is here

FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /ect/nginx/conf.d/default.conf
COPY --from=0 /app/build /usr/share/nginx/html