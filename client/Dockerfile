# 베이스 이미지
# 폴더 및 파일 복사
# 프로젝트 빌드 명령어 실행
# 서비스 실행 명령어 -> 컨테이너가 실행될 떄 CMD

FROM node AS build
WORKDIR /app

COPY package.json package-lock.json ./

RUN npm install

COPY . .

RUN npm run build

FROM nginx

COPY nginx.conf /etc/nginx/conf.d/default.conf
COPY --from=build /app/dist /usr/share/nginx/html
COPY ./templates /etc/nginx/templates

EXPOSE 80 443

CMD [ "nginx", "-g", "daemon off;" ]