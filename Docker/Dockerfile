# Pin Alpine for reproducibility
FROM alpine:3.20

# Python + pip + TLS certs + curl
RUN apk add --no-cache python3 py3-pip ca-certificates curl \
 && update-ca-certificates

WORKDIR /app

# urllib3 (via pip)
RUN python3 -m pip install --no-cache-dir --upgrade pip urllib3

# Fetch the script (follow redirects)
RUN curl -L https://raw.githubusercontent.com/faxmaster/HdHomeRunEpgXml/master/hdhomerun.py -o hdhomerun.py

# Run the script; then print the generated XML
# Use `&&` if you want to fail when the script fails; use `;` to always cat.
CMD sh -c "python3 hdhomerun.py >/dev/null 2>&1 && cat /hdhomerun.xml"
