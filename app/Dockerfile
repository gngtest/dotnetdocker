#FROM dotnet/dotnet-31-runtime-rhel7:3.1-11
#FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS runtime
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
RUN cp /usr/share/zoneinfo/Europe/Istanbul /etc/localtime
RUN echo "Europe/Istanbul" > /etc/timezone


#RUN sed -i 's/TLSv1.2/TLSv1.0/g' /etc/ssl/openssl.cnf
RUN apt-get update && apt-get install -y nginx

WORKDIR /app
COPY bin/Release/netcoreapp3.1/publish .
 
COPY ./startup.sh .
RUN chmod 755 /app/startup.sh
 
RUN rm /etc/nginx/nginx.conf
COPY nginx.conf /etc/nginx
 
ENV ASPNETCORE_URLS http://+:5000
EXPOSE 5000 80

CMD ["sh", "/app/startup.sh"]
