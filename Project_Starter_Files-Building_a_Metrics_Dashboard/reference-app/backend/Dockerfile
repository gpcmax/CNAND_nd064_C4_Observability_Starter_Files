FROM python:3.7-slim

ENV APP_HOME /app
WORKDIR $APP_HOME
COPY . ./

ARG PROJECT_ID
ENV PROJECT_ID ${PROJECT_ID}

EXPOSE 5000

RUN apt-get update && \
    pip install --upgrade pip && \
    pip install -r requirements.txt

CMD [ "python", "app.py" ]