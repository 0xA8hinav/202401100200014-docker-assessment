FROM python:3.12-slim-bookworm
WORKDIR /app
ARG APP_VERSION=dev
ENV APP_VERSION=${APP_VERSION}
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
COPY app.py .
RUN useradd -m appuser && chown -R appuser /app
USER appuser
CMD ["python", "app.py"]
