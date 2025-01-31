FROM node:18 AS build

WORKDIR /app

COPY ["app/Azure_Exam3.Client/package*.json", "./"]

RUN npm install

COPY app/Azure_Exam3.Client/ ./

RUN npm run build

FROM nginx:alpine
COPY --from=build /app/dist /usr/share/nginx/html

EXPOSE 80
