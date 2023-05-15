FROM postman/newman:latest

RUN npm install -g newman-reporter-htmlextra

WORKDIR /etc/newman

ENV COLLECTIONID=""
ENV POSTMANAPIKEY=""
ENV ENVIRONMENTID=""

ENTRYPOINT ["sh", "-c", "mkdir -p ~/postman-dir || exit 1 && newman run -k \"https://api.getpostman.com/collections/$COLLECTIONID?apikey=$POSTMANAPIKEY\" -e \"https://api.getpostman.com/environments/$ENVIRONMENTID?apikey=$POSTMANAPIKEY\" -r htmlextra --reporter-htmlextra-browserTitle 'Test Report' --reporter-htmlextra-title 'Report Dashboard' --reporter-htmlextra-logs --reporter-htmlextra-displayProgressBar && echo 'Report is at location ~/postman-dir/newman'"]

VOLUME ["~/postman-dir"]