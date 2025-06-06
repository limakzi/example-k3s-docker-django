FROM python:3.13  

EXPOSE 8080

## {{
ENV APP_USERNAME "django"
ENV APP_USERNAME_ID "1000"
ENV APP_GROUPNAME  "djnago"
ENV APP_GROUP_ID "1000"
ENV APP_DIRECTORY "/opt/django"
## }}

## {{
RUN groupadd -g "${APP_GROUP_ID}" "${APP_GROUPNAME}"    && \
    useradd -m -d "${APP_DIRECTORY}" -G "${APP_GROUPNAME}" "${APP_USERNAME}"
USER "${APP_USERNAME}"
ENV PATH "$PATH:$HOME/.local/bin/"
## }}


## {{
RUN pip install --upgrade pip 
COPY requirements.txt  ./
RUN pip install --no-cache-dir -r requirements.txt
## }}

COPY . ./

CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]
