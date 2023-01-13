# Stage 1: Build
FROM python:3.8-slim-buster as build
ENV PYTHONUNBUFFERED=1

WORKDIR /var/www
COPY requirements.txt .
RUN python3 -m pip install --no-cache-dir -r requirements.txt
RUN python3 -m pip install --no-cache-dir gunicorn

# Stage 2: Production
FROM python:3.8-slim-buster as production
ENV PYTHONUNBUFFERED=1

# Copy over the installed Python packages from the build stage
COPY --from=build /usr/local/lib/python3.8/site-packages /usr/local/lib/python3.8/site-packages
COPY --from=build /usr/local/bin/gunicorn /usr/local/bin/

# Copy the application code
COPY app.py .

# Set the entrypoint to run the application with gunicorn
# This entrypoint will be replaced by the one in the docker-compose.yml file when running the application with docker-compose
ENTRYPOINT ["gunicorn", "app:app", "--bind=0.0.0.0:8000", "--workers=4", "--log-level=debug", "--reload"]
