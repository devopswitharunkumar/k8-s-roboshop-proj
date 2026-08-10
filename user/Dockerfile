FROM node:current-alpine3.23
EXPOSE 8080
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
WORKDIR /opt/server
RUN chown roboshop:roboshop /opt/server
USER roboshop
WORKDIR /opt/server
# ENV MONGO=true        #pass it from k8's configmap  
COPY package.json /opt/server
COPY server.js /opt/server
RUN npm install
CMD [ "node", "server.js"]


