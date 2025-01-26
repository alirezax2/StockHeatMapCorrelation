# Install uv
FROM python:3.12-slim
COPY --from=ghcr.io/astral-sh/uv:latest /uv /uvx /bin/


# Install dependencies
RUN --mount=type=cache,target=/root/.cache/uv \
    --mount=type=bind,source=uv.lock,target=uv.lock \
    --mount=type=bind,source=pyproject.toml,target=pyproject.toml \
    uv sync --frozen --no-install-project

# Copy the project into the image
ADD . /app

# Change the working directory to the `app` directory
WORKDIR /app

# Sync the project
RUN --mount=type=cache,target=/root/.cache/uv \
    uv sync --frozen

COPY pyproject.toml .
RUN uv pip install -r pyproject.toml
COPY . .

# Run the application
# Presuming there is a `my_app` command provided by the project
CMD ["uv", "run", "hello.py"]