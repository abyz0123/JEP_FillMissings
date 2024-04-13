# Use the official Python image from the Docker Hub
FROM python:3.9

# Install R
RUN apt-get update && apt-get install -y \
    r-base \
    libssl-dev \
    libcurl4-openssl-dev \
    libxml2-dev

# Install Jupyter and dependencies
RUN pip install jupyter

# Install Stata
ARG STATA_LICENSE_KEY
RUN curl -o /tmp/stata.tgz https://download.stata.com/download/dmg/dmg-catA/v17/install-macos/stata17linux64.tar.gz \
    && tar -xzvf /tmp/stata.tgz -C /usr/local \
    && /usr/local/stata17/install -silent ${STATA_LICENSE_KEY}

# Expose port for Jupyter notebook
EXPOSE 8888

# Set working directory
WORKDIR /workspace

# Start Jupyter notebook
CMD ["jupyter", "notebook", "--ip=0.0.0.0", "--port=8888", "--no-browser", "--allow-root"]
