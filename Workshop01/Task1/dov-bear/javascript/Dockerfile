ARG NODE_VER=17

FROM node:${NODE_VER}

#begin of build stage
ARG APP_DIR=/app

#cd in APP_DIR
WORKDIR ${APP_DIR}

#ADD main.js . 
#ADD package.json . 
#ADD package-locl.json . 
#ADD public public
#ADD views views

#add all folders and files.
ADD . .

RUN npm i

#end of build stage

#start of run stage
ENV INSTANCE_NAME=NodeJS
ENV INSTANCE_HASH=NodeJSHASH
ENV PORT=3000

EXPOSE ${PORT}

HEALTHCHECK --interval=30s --timeout=30s --start-period=5s --retries=3 \
    CMD curl http://localhost:${PORT}/htealthz || exit 1


ENTRYPOINT ["node", "main.js"]

#end of run stage