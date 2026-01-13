# Base image: Microsoft Dev Containers Python 3.13 (used by GitHub Codespaces)
FROM mcr.microsoft.com/devcontainers/python:3.13-bullseye

# OCI labels for GitHub Container Registry
LABEL org.opencontainers.image.source=https://github.com/zoltanctoth/ceu-modern-data-platforms
LABEL org.opencontainers.image.description="CEU Modern Data Platforms Development Container"

# Switch to vscode user for UV installation
USER vscode

# Install UV package manager
RUN curl -LsSf https://astral.sh/uv/install.sh | sh

# Add UV to PATH
ENV PATH="/home/vscode/.local/bin:$PATH"

# Copy project files for dependency installation
COPY --chown=vscode:vscode pyproject.toml uv.lock /workspaces/ceu-modern-data-platforms/

# Create virtual environment and install dependencies using UV
WORKDIR /workspaces/ceu-modern-data-platforms
RUN uv sync --frozen || uv sync
