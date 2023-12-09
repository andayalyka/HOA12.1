FROM python:3.8
RUN pip3 install --upgrade pip
# Create a directory named tempdir
mkdir tempdir

# Create subdirectories named templates and static inside tempdir
mkdir tempdir/templates
mkdir tempdir/static

# Copy the file sample_app.py to tempdir
cp sample_app.py tempdir/.

# Copy all files from the templates directory to tempdir/templates
cp templates/* tempdir/templates/.

# Copy all files from the static directory to tempdir/static
cp static/* tempdir/static/.

# Start building the Docker image from the official Python image
FROM python

# Install the Flask package using pip inside the Docker image
RUN pip3 install flask

# Copy the contents of the static directory to /home/myapp/static inside the Docker image
COPY ./static /home/myapp/static/

# Copy the contents of the templates directory to /home/myapp/templates inside the Docker image
COPY ./templates /home/myapp/templates/

# Copy the file sample_app.py to /home/myapp/ inside the Docker image
COPY sample_app.py /home/myapp/

# Expose port 8080 to the outside world
EXPOSE 8080

# Specify the command to run when the Docker container starts
CMD python3 /home/myapp/sample_app.py
