FROM node:15 as builder

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

RUN npm run build

FROM node:15 as deploy

WORKDIR /app

COPY --from=builder /app/build ./build

RUN npm install -g serve

EXPOSE 5000

ENTRYPOINT ["serve", "-s", "build", "-l", "5000"]