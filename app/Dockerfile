FROM dotnet/dotnet-31-runtime-rhel7:3.1-11

RUN apt-get update
RUN apt-get install -y nginx

WORKDIR /app

RUN ["dotnet", "build"]

COPY bin/Debug/netcoreapp3.1/* .

COPY ./startup.sh .
RUN chmod 755 /app/startup.sh

RUN rm /etc/nginx/nginx.conf
COPY nginx.conf /etc/nginx

ENV ASPNETCORE_URLS http://+:5000
EXPOSE 5000 80

CMD ["sh", "/app/startup.sh"]
