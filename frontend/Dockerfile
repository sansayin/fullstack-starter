FROM node:16.13.1-alpine3.14

WORKDIR /usr/src/app

COPY ["package.json", "package-lock.json",".env", "env.d.ts" , "index.html","package.json.express","pnpm-lock.yaml","tsconfig.json","tsconfig.node.json","vite.config.ts", "./"]

COPY ./src ./src

RUN npm install

EXPOSE 3000
CMD npm run dev

