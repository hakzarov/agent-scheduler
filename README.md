# agent-scheduler

Schedules agents in a distributed blockchain based super-network to, mainly improve true open AIs (in contrast to companies like Closed AI).

## Prerequisites

- Python 3.13+
- Poetry (for dependency management)

## Installation

### 1. Install Poetry

If you don't have Poetry installed, install it using one of these methods:

```bash
# Using pip
pip install poetry

# Using the official installer (recommended)
curl -sSL https://install.python-poetry.org | python3 -

# On macOS using Homebrew
brew install poetry
```

### 2. Install Dependencies

```bash
# Install all dependencies
poetry install

# Install only production dependencies
poetry install --only main
```

## Usage

### Running the Application

```bash
# Activate the virtual environment and run
poetry run python -m agent_scheduler.main

# Or activate the shell and run directly
poetry shell
python -m agent_scheduler.main
```

### Development

```bash
# Add a new dependency
poetry add package-name

# Add a development dependency
poetry add --group dev package-name

# Remove a dependency
poetry remove package-name

# Update dependencies
poetry update

# Show dependency tree
poetry show --tree

# Check for outdated packages
poetry show --outdated
```

### Virtual Environment

```bash
# Activate the virtual environment
poetry shell

# Show virtual environment info
poetry env info

# List virtual environments
poetry env list
```

## Project Structure

```
agent-scheduler/
├── agent_scheduler/          # Main package
│   └── main.py              # Entry point
├── pyproject.toml           # Poetry configuration and dependencies
├── poetry.lock              # Locked dependency versions
└── README.md                # This file
```

## Contributing

1. Fork the repository
2. Create a feature branch
3. Install dependencies: `poetry install`
4. Make your changes
5. Run tests (when available): `poetry run pytest`
6. Submit a pull request
