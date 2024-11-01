FROM python:3.12.0-slim-bookworm

ENV PYTHONBUFFERED 1
ENV PYTHONWRITEBYTECODE 1

# Set the working directory
WORKDIR /server

# Install the requirements
COPY requirements.txt /server/
RUN pip3 install -r requirements.txt

# Copy the rest of the files
COPY manage.py /server/
COPY package.json /server/
COPY database /server/database
COPY djangoproj /server/djangoproj
COPY djangoapp /server/djangoapp
COPY frontend /server/frontend
COPY . /server/

EXPOSE 8000

RUN chmod +x /server/entrypoint.sh

ENTRYPOINT ["/bin/bash", "/server/entrypoint.sh"]

CMD ["gunicorn", "--bind", ":8000", "--workers", "3", "djangoproj.wsgi"]
