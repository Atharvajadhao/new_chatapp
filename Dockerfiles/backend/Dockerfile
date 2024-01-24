FROM python:3.6
ENV DATABASE_NAME chat_db
ENV DATABASE_USER admin
ENV DATABASE_PASS admin
ENV DATABASE_HOST database
RUN apt-get update
RUN apt-get install --yes python3-pip git
WORKDIR /root/
RUN git clone https://github.com/Atharvajadhao/new_chatapp.git
WORKDIR /root/new_chatapp
RUN pip3 install -r requirements.txt
RUN pip3 install mysqlclient
EXPOSE 8000
WORKDIR /root/new_chatapp/fundoo/
ENTRYPOINT  python3 manage.py migrate && python3 manage.py runserver 0.0.0.0:8000
