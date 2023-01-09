# #first task
# FROM python:alpine3.15   
# RUN apk add python2  && apk add npm && apk add nodejs 
# RUN wget https://bootstrap.pypa.io/pip/2.7/get-pip.py && python2.7 get-pip.py 
# # RUN python -m ensurepip --upgrade #PIP2 INSTALL
# COPY requirements.txt .
# RUN pip2 install -r requirements.txt
# COPY . .
# # COPY package.json .
# # COPY package-lock.json .
# RUN npm install
# RUN npm run build 

# ENTRYPOINT python2 app.py

#smaller image

FROM python:alpine3.15 AS build-stage
RUN apk add npm && apk add nodejs 

WORKDIR /app
# COPY requirements.txt .
# RUN pip2 install -r requirements.txt
COPY . .
# COPY package.json .
# COPY package-lock.json .
RUN npm install
RUN npm run build 

#ibbd/python2-scrapy-v8
#docker pull python:2.7-slim-stretch
# FROM python:2.7-stretch
# FROM python:alpine3.15
# RUN apk add python2
# FROM python:2.7-slim-stretch
FROM python:alpine3.15
COPY --from=build-stage /app .
RUN apk add python2
RUN wget https://bootstrap.pypa.io/pip/2.7/get-pip.py && python2.7 get-pip.py 
# RUN python -m ensurepip --upgrade #PIP2 INSTALL
RUN pip2 install -r requirements.txt
ENTRYPOINT python2 app.py





