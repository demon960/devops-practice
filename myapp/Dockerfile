cat > /root/devops-practice/myapp/Dockerfile << 'EOF'
FROM python:3.11-slim

# Метаданные для Docker Hub
LABEL org.opencontainers.image.title="DevOps Practice App"
LABEL org.opencontainers.image.description="Flask application for DevOps learning"
LABEL org.opencontainers.image.version="1.0.0"
LABEL org.opencontainers.image.authors="Your Name"
LABEL org.opencontainers.image.source="https://github.com/demon960/devops-practice"
LABEL org.opencontainers.image.licenses="MIT"

WORKDIR /app

# Аргументы сборки
ARG BUILD_DATE
ARG VCS_REF
ARG VERSION=1.0.0

LABEL org.label-schema.build-date=$BUILD_DATE \
      org.label-schema.name="DevOps Practice App" \
      org.label-schema.description="Flask application" \
      org.label-schema.url="https://github.com/demon960/devops-practice" \
      org.label-schema.vcs-ref=$VCS_REF \
      org.label-schema.vcs-url="https://github.com/demon960/devops-practice.git" \
      org.label-schema.version=$VERSION \
      org.label-schema.schema-version="1.0"

# Устанавливаем переменные окружения
ENV PYTHONUNBUFFERED=1
ENV PYTHONDONTWRITEBYTECODE=1

# Копируем зависимости
COPY requirements.txt .

# Устанавливаем зависимости
RUN pip install --no-cache-dir -r requirements.txt

# Копируем приложение
COPY app.py .

# Открываем порт
EXPOSE 5000

# Запускаем приложение
CMD ["python", "app.py"]
EOF
