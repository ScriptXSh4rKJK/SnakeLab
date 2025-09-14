# syntax=docker/dockerfile:1
FROM python:3.11-slim

WORKDIR /app

RUN apt-get update -y && apt-get install -y --no-install-recommends \
    build-essential \
    libssl-dev \
    libffi-dev \
  && rm -rf /var/lib/apt/lists/*

# requirements из подпапки
COPY SnakeLab/SnakeLab/py_learn_site/requirements.txt ./requirements.txt
RUN python -m pip install --upgrade pip setuptools wheel && \
    pip install --no-cache-dir -r requirements.txt

# копируем код из подпапки
COPY SnakeLab/SnakeLab/py_learn_site/ ./

ENV PYTHONUNBUFFERED=1 \
    PORT=8080

EXPOSE 8080
CMD ["python", "app.py"]
