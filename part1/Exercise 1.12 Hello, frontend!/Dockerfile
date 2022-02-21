FROM node:16

EXPOSE 5000

WORKDIR /usr/src/app

COPY . .

RUN npm install && npm run build && npm install -g serve

CMD ["serve", "-s", "-l", "5000", "build"]