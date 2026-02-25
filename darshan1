FROM nginx:latest
WORKDIR /app
RUN rm -rf /user/share/nginx/html/*
COPY html/ /user/share/nginx/html.index
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]

