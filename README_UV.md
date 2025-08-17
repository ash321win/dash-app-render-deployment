# Using UV for Dependency Management

This project now uses [uv](https://github.com/astral-sh/uv) for Python dependency management, which is a fast Python package installer and resolver.

## Quick Start

### Install uv (if not already installed)
```bash
# Windows (PowerShell)
irm https://astral.sh/uv/install.ps1 | iex

# macOS/Linux
curl -LsSf https://astral.sh/uv/install.sh | sh
```

### Setup the project
```bash
# Navigate to the project directory
cd dash-app-render-deployment

# Install dependencies
uv sync

# Activate the virtual environment
uv shell
```

### Common uv commands

```bash
# Install dependencies
uv sync

# Add a new dependency
uv add package-name

# Add a development dependency
uv add --dev package-name

# Remove a dependency
uv remove package-name

# Update dependencies
uv lock --upgrade

# Run a command in the virtual environment
uv run python app.py

# Activate the virtual environment
uv shell
```

## Project Structure

- `pyproject.toml` - Project configuration and dependencies
- `uv.lock` - Lock file with exact versions (auto-generated)
- `requirements.txt` - Exported requirements for deployment compatibility

## Benefits of using uv

1. **Fast**: Much faster than pip for dependency resolution and installation
2. **Reliable**: Deterministic builds with lock files
3. **Modern**: Uses pyproject.toml for project configuration
4. **Compatible**: Can export to requirements.txt for deployment
5. **Cross-platform**: Works on Windows, macOS, and Linux

## Deployment

For deployment platforms that require requirements.txt, the file is automatically generated and kept up to date:

```bash
uv export --format requirements-txt --output-file requirements.txt
```

This ensures compatibility with platforms like Render, Heroku, etc.
