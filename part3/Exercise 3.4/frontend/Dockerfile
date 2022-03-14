FROM ubuntu:18.04

EXPOSE 5000

WORKDIR /usr/src/app

COPY . .

RUN apt-get update && apt-get install curl -y  && \
    curl -sL https://deb.nodesource.com/setup_16.x | bash && \ 
    apt install -y nodejs && \
    npm install && \
    REACT_APP_BACKEND_URL=http://localhost/api npm run build && \
    npm install -g serve && \
    useradd -m appuser && \
    apt-get purge -y --auto-remove curl && \
    rm -rf /var/lib/apt/lists/*

USER appuser

CMD ["serve", "-s", "-l", "5000", "build"]