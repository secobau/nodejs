FROM alpine/git AS clone
WORKDIR /app
RUN git clone https://github.com/secobau/nodejs

FROM node:alpine
WORKDIR /app
COPY --from=clone /app/nodejs/express-hello-world /app 
RUN npm init -y && npm install $(awk -F"'" '/require\(.[^\.]/{print $2}' index.js)
#RUN npm install
ENTRYPOINT ["node"]
CMD ["index.js"]

# docker build --tag express-hello-world:alpine https://raw.githubusercontent.com/secobau/nodejs/master/express-hello-world/Dockerfile.txt
# docker container run --name express-hello-world --detach --publish 8080:8080 express-hello-world:alpine
