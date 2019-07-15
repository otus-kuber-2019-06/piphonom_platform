FROM nginx:alpine

WORKDIR /app

COPY nginx.conf /etc/nginx/nginx.conf
EXPOSE 8000
USER 1001

ENTRYPOINT ["nginx", "-g", "daemon off;"]