FROM python:3.11-slim

WORKDIR /app

COPY . /app

RUN pip install -r requirements.txt
RUN pip install --upgrade pip wheel==0.46.2 jaraco.context==6.1.0
RUN pip install --no-cache-dir -r requirements.txt

EXPOSE 5002 

# 5002 this is for local dev

CMD ["python", "app.py"]
