FROM python:3.11-slim-bullseye

ENV PIP_DISABLE_PIP_VERSION_CHECK 1
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

WORKDIR /code

RUN apt update -y 
RUN apt-get install libpq-dev python3-dev wget -y

COPY requirements.txt .
RUN pip3 install -r requirements.txt

COPY requirements_test.txt .
RUN pip3 install -r requirements_test.txt

RUN python3 -m spacy download en_core_web_trf

COPY . .
EXPOSE 8030

CMD [ "python", "main.py" ]
