FROM python:3.8-buster

WORKDIR /app/

ARG GITHUB_TOKEN

EXPOSE 80

ENV POETRY_VERSION=1.0.8

#System dependencies
RUN pip install "poetry==$POETRY_VERSION"

COPY pyproject.toml /app/
COPY poetry.lock /app/

ENV GITHUB_TOKEN=$GITHUB_TOKEN

RUN poetry install --no-dev

COPY . /app/

CMD ["poetry", "run", "uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"]
