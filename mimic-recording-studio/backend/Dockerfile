# Base image
FROM python:3.6-alpine3.6

# Install system dependencies for Python packages
RUN apk update && apk add --no-cache ffmpeg make automake gcc g++ subversion python3-dev sqlite-dev musl-dev libffi-dev

# Upgrade pip
RUN pip install --upgrade pip

# Set the working directory to /src
WORKDIR /src

# Copy the requirements.txt file into the container at /src
COPY requirements.txt /src/

# Environment variable to avoid building `peewee` C extensions
ENV PW_NO_EXTENSION=1

# Install the Python dependencies from requirements.txt
RUN pip install --no-cache-dir -r requirements.txt

# Copy the rest of your application's code into the container at /src
COPY . /src

# Make sure start_prod.sh is executable
RUN chmod +x /src/start_prod.sh

# Command to run when the container starts. Adjusted to explicitly call with sh, even though it might be redundant.
CMD ["sh", "/src/start_prod.sh"]
