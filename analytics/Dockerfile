FROM python:3.10-slim-buster

USER root

WORKDIR /src

COPY ./requirements.txt requirements.txt

ENV DB_USERNAME=myuser
ENV DB_PASSWORD=mypassword


# Dependencies required for psycopg2 (used for Postgres client)
RUN apt update -y && apt install -y build-essential libpq-dev

# Dependencies are installed during build time in the container itself so we don't have OS mismatch
RUN pip install --upgrade pip setuptools wheel
RUN pip install -r requirements.txt

COPY . .

CMD python app.py