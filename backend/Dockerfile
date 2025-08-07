FROM python:3.11-slim

WORKDIR /app

# Установить системные зависимости (для сборки psycopg2-binary)
RUN apt-get update && apt-get install -y \
    build-essential \
    libpq-dev \
    gcc

COPY requirements.txt .

RUN pip install gunicorn==23.0.0

RUN pip install -r requirements.txt --no-cache-dir

COPY . .

CMD ["gunicorn", "--bind", "0.0.0.0:8000", "backend.wsgi:application"]
