FROM python:3.11-slim
LABEL maintainer="arzumanian@lab.local"
LABEL version="1.0"
WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
COPY app/ ./app/
EXPOSE 8041
CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8041"]
