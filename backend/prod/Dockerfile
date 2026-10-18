FROM python:3.11-slim
WORKDIR /app
ENV PYTHONUNBUFFERED=1
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt gunicorn
COPY . .
RUN useradd -m appuser && chown -R appuser /app
USER appuser
EXPOSE 3002
CMD ["gunicorn", "-b", "0.0.0.0:3002", "-w", "2", "--access-logfile", "-", "app:app"]