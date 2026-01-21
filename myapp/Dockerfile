# Этап 1: Сборка (Builder)
FROM python:3.11-slim AS builder
WORKDIR /app
COPY requirements.txt .
RUN pip install --user --no-cache-dir -r requirements.txt

# Этап 2: Финальный образ (Runtime)
FROM python:3.11-slim
WORKDIR /app

# Копируем только установленные пакеты из этапа builder
COPY --from=builder /root/.local /root/.local
# Копируем исходный код
COPY app.py .

# Делаем так, чтобы python и pip были доступны в PATH
ENV PATH=/root/.local/bin:$PATH
# Открываем порт
EXPOSE 5000
# Запускаем приложение
CMD ["python", "app.py"]
