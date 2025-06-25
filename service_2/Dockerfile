FROM python:3.10-alpine

# Install system packages for building deps
RUN apk add --no-cache curl bash gcc musl-dev libffi-dev

# Install uv (fast Python package manager)
RUN curl -Ls https://astral.sh/uv/install.sh | sh

# Add uv to PATH
ENV PATH="/root/.local/bin:$PATH"

WORKDIR /app

COPY . .

# Install all packages from requirements.txt
RUN uv pip install --system -r requirements.txt

EXPOSE 8002

CMD ["python", "app.py"]

