FROM python:3-slim-bullseye
RUN apt update -y && apt install build-essential -y
RUN pip install pip wheel --upgrade 
RUN pip install boto3
RUN pip install jupyter

CMD ["jupyter", "notebook", "--allow-root"]
