# Use the official Python image from the Docker Hub
# FROM python:3
FROM python:3.10.12

# Set the working directory in the container
WORKDIR /workspace

# Copy the requirements file into the container
COPY requirements.txt .

# Install the required packages
RUN pip install --no-cache-dir -r requirements.txt

##. for monospace font (used in long vertical ticklabels) 
##. Recommended Safe Approach for DevContainers
RUN apt-get update && apt-get install -y \
    fonts-dejavu-core \
    fonts-liberation \
    xfonts-base \
    && rm -rf /var/lib/apt/lists/* \
    && fc-cache -f -v

# Copy the rest of the application code into the container
COPY . .

# Expose the port for Jupyter Notebook
EXPOSE 8888

# Run Jupyter Notebook
CMD ["jupyter", "notebook", "--ip=0.0.0.0", "--port=8888", "--no-browser", "--allow-root"]
