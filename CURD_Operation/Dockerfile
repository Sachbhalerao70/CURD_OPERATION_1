
FROM python:3.10

# Set environment variables
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

# Set the working directory in the container
WORKDIR /app

# Copy the current directory contents into the container at /app
COPY . /app

# Install any needed packages specified in requirements.txt
COPY requirements.txt /app/
RUN pip install --no-cache-dir -r requirements.txt

# Run collectstatic
RUN python manage.py collectstatic --noinput

RUN python manage.py makemigrations



# Make port 8000 available to the world outside this container
EXPOSE 8000

# Define the command to run on container start
CMD ["gunicorn", "--bind", "0.0.0.0:8000", "CURD_Operation.wsgi:application"]