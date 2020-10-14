FROM nodered/node-red

WORKDIR /usr/src/node-red

COPY node-red-contrib-covid19api .

RUN npm install ./ node-red-contrib-covid19api

# Chown, install devtools & Clean up
RUN chown -R node-red:root /usr/src/node-red && \
    /tmp/install_devtools.sh && \
    rm -r /tmp/*


USER node-red

ENV NODE_RED_VERSION=$NODE_RED_VERSION \
    NODE_PATH=/usr/src/node-red/node_modules:/data/node_modules \
    FLOWS=flows.json

EXPOSE 1880

# Add a healthcheck (default every 30 secs)
# HEALTHCHECK CMD curl http://localhost:1880/ || exit 1

ENTRYPOINT ["npm", "start", "--cache", "/data/.npm", "--", "--userDir", "/data"]


