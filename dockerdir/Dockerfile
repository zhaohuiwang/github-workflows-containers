FROM alpine
# Adding bash to Alpine Docker image
RUN apk add --no-cache bash
WORKDIR /app
COPY entrypoint.sh .
RUN chmod +x entrypoint.sh
ENTRYPOINT [ "/app/entrypoint.sh" ]

# https://docs.docker.com/build/building/best-practices/