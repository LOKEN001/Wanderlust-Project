#------------------stage -- backendBuilder -------------------

FROM node:21 As backendBuilder

WORKDIR /apps

COPY package*json ./

RUN npm install

COPY . .

#----------------stage2 slim-image ------------------------

FROM node:21-slim 

WORKDIR /apps

COPY --from=backendBuilder /apps .

COPY .env.docker .env

EXPOSE 8080

CMD ["npm", "start"]
