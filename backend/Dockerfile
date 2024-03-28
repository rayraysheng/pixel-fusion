# Development stage
FROM python:3.10 AS development
WORKDIR /app
COPY ./backend/requirements.txt ./
RUN pip3 install -r requirements.txt
RUN pip install --upgrade Flask Werkzeug
RUN pip install --upgrade Flask-Cors
COPY ./backend/src .
CMD ["python", "app.py"]

# Production stage
FROM development as production
RUN pip3 install gunicorn
CMD ["gunicorn", "-w", "2", "-c", "config.py", "app:app"]
