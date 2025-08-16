FROM python:3.12-alpine

RUN apk add --no-cache curl ca-certificates && update-ca-certificates
RUN pip install --no-cache-dir urllib3
RUN curl -fsSL https://raw.githubusercontent.com/faxmaster/HdHomeRunEpgXml/master/hdhomerun.py \
    -o /hdhomerun.py

CMD ["sh","-c","python /hdhomerun.py >/dev/null 2>&1 && cat /hdhomerun.xml"]
