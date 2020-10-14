FROM nodered/node-red

WORKDIR /usr/src/node-red

COPY node-red-contrib-covid19api .

RUN   chgrp -R 0 /opt/app-root && \
      chgrp -R 0 /usr/src/node-red
      chmod -R g=u /opt/app-root \
      chmod -R g=u /usr/src/node-red

RUN npm install ./node-red-contrib-covid19api

USER 1001

ENV NODE_RED_VERSION=$NODE_RED_VERSION \
    NODE_PATH=/usr/src/node-red/node_modules:/data/node_modules \
    FLOWS=flows.json

EXPOSE 1880

# Add a healthcheck (default every 30 secs)
# HEALTHCHECK CMD curl http://localhost:1880/ || exit 1

ENTRYPOINT ["npm", "start", "--cache", "/data/.npm", "--", "--userDir", "/data"]


