FROM node:18-alpine AS build
WORKDIR /app

COPY package-lock.json package.json ./
RUN npm ci --legacy-peer-deps

COPY . .
RUN npm run build
FROM node:18-alpine AS production
WORKDIR /app
COPY --from=build /app/build /app/build

EXPOSE 3000
RUN npm install -g serve
CMD ["serve", "-s", "build", "--listen", "0.0.0.0:3000"]

