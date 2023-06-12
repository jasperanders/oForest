FROM docker.io/continuumio/anaconda3:latest

# Directory setup
RUN mkdir /src
WORKDIR /src

COPY ./src/ /src/
COPY ./.resetdb.sh /src/ 

RUN apt-get update
RUN apt-get -y install libpq-dev gcc

RUN pip install -r requirements.txt

EXPOSE 8000

CMD [ "otree", "prodserver", "8000"] 
