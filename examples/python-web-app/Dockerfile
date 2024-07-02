FROM ubuntu

WORKDIR /app

COPY requirements.txt /app
COPY devops /app

RUN apt-get update && \
    apt-get install -y python3 python3-pip && \
    pip install -r requirements.txt && \
    cd devops

ENTRYPOINT ["python3"]
CMD ["manage.py", "runserver", "0.0.0.0:8000"]

// for windows wsl since the environment in Docker container is managed externally and restricts direct installation of Python packages system-wide using pip.
This can be resolved by creating and using a virtual environment for package installation within the Docker container.

FROM ubuntu

WORKDIR /app

COPY requirements.txt /app
COPY devops /app

# Update package list and install Python3, pip, and venv
RUN apt-get update && \
    apt-get install -y python3 python3-pip python3-venv

# Create and activate a virtual environment, install dependencies
RUN python3 -m venv venv && \
    . venv/bin/activate && \
    pip install --upgrade pip && \
    pip install -r requirements.txt

ENV PATH="/app/venv/bin:$PATH"

ENTRYPOINT ["python3"]
CMD ["manage.py", "runserver", "0.0.0.0:8000"]



