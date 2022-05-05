FROM python:3.10

RUN apt-get update                      \
    && apt install -y                   \
           build-essential              \
    && rm -rf /var/lib/apt/lists/*

ADD requirements.txt /type-deduction-src/requirements.txt
WORKDIR /type-deduction-src/
RUN pip3 install -r requirements.txt

ADD . /type-deduction-src/

ENTRYPOINT ["python3", "/type-deduction-src/main.py"]
