#--------------------stage-nodeBuilder------------------

FROM node:21 As nodeBuilder

WORKDIR /apps

COPY package*.json ./

RUN npm install 

COPY . .

#-------------------stage-call--------------------------

FROM node:21-slim 

WORKDIR /apps

COPY --from=nodeBuilder /apps .

COPY .env.docker .env.local

EXPOSE 5173

CMD ["npm", "run", "dev", "--", "--host"]


