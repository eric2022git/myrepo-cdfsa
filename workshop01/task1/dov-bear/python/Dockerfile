# syntax=docker/dockerfile:1

FROM python:slim-buster

WORKDIR /app

COPY requirements.txt requirements.txt
RUN pip3 install -r requirements.txt

COPY . .

ENV APP_PORT=3000
EXPOSE ${APP_PORT}

HEALTHCHECK --interval=30s --timeout=30s --start-period=5s --retries=3 CMD curl -s -f http://localhost:${APP_PORT} || exit 1

CMD [ "python3", "-m" , "flask", "run", "--host=0.0.0.0"]