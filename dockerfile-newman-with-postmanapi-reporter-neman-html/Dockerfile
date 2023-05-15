FROM postman/newman:latest

RUN npm install -g newman-reporter-html

WORKDIR /etc/newman

ENV COLLECTIONID=""
ENV POSTMANAPIKEY=""
ENV ENVIRONMENTID=""

ENTRYPOINT ["sh", "-c", "mkdir -p ~/postman-dir || exit 1 && newman run -k \"https://api.getpostman.com/collections/$COLLECTIONID?apikey=$POSTMANAPIKEY\" -e \"https://api.getpostman.com/environments/$ENVIRONMENTID?apikey=$POSTMANAPIKEY\" -r html && echo 'Report is at location ~/postman-dir/newman'"]

VOLUME ["~/postman-dir"]