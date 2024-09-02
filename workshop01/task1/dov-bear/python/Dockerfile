ARG PYTHON_VER=3.12
FROM python:${PYTHON_VER}


# Create a dir /app and cd /app
WORKDIR /app

# Copy from local container
COPY main.py .
COPY utils.py .
COPY requirements.txt .
COPY public public
COPY templates templates

# install node modules
RUN pip install --no-cache-dir -r requirements.txt

# Define environment variables
ENV PORT=3000 INSTANCE_NAME=my-dov_bear INSTANCE_HASH=my-dov-bear-hash
ENV FLASK_APP=main.py
ENV FLASK_RUN_HOST=0.0.0.0

HEALTHCHECK --interval=30s --timeout=5s --start-period=5s --retries=3 \
    CMD curl -s localhost:${PORT}/healthz || exit 1

# What are th exposed port
EXPOSE ${PORT}

# Run the application
ENTRYPOINT python main.py