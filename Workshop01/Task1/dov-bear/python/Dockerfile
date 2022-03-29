ARG PYTHON_VER=3.10.3


FROM python:${PYTHON_VER}

#begin of build stage
ARG APP_DIR=/app

#cd in APP_DIR
WORKDIR ${APP_DIR}


#add all folders and files.
ADD . .

RUN pip install -r requirements.txt

#end of build stage

#start of run stage
ENV INSTANCE_NAME=Python
ENV INSTANCE_HASH=PythonHASH
ENV PORT=3000

EXPOSE ${PORT}

HEALTHCHECK --interval=30s --timeout=30s --start-period=5s --retries=3 \
    CMD curl http://localhost:${PORT}/htealthz || exit 1


ENTRYPOINT ["python", "main.py"]

#end of run stage