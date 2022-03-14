FROM node:16-alpine

EXPOSE 5000

WORKDIR /usr/src/app

COPY . .

RUN apk update --no-cache && \
    npm install && \
    REACT_APP_BACKEND_URL=http://localhost/api npm run build && \
    npm install -g serve && \
    adduser -S appuser

USER appuser

CMD ["serve", "-s", "-l", "5000", "build"]