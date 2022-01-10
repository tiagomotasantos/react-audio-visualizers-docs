FROM jekyll/jekyll
WORKDIR /app
COPY . .
RUN chmod -R 777 .
EXPOSE 4000
CMD ["jekyll", "serve"]