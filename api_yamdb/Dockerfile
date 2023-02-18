FROM python:3.7.16-slim

WORKDIR /app/api_yamdb/

COPY api_yamdb/requirements.txt /app

RUN pip install -r /app/requirements.txt --no-cache-dir

COPY ../ /app

ENV PYTHONUNBUFFERED=1 \
    PYTHONDONTWRITEBYTECODE=1 \
    DJANGO_SECRET_KEY=DJANGO_SECRET_KEY

RUN python manage.py collectstatic --no-input  

RUN addgroup --system app && \
    adduser --system --ingroup app app

CMD ["gunicorn", "api_yamdb.wsgi:application", "--bind", "0:8000" ]
