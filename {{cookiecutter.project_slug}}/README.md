# {{ cookiecutter.project_name }}

Author: {{ cookiecutter.author_name }}

## Setup

```bash
# Install dependencies with uv
uv sync --extra dev

# Set up pre-commit hooks
uv run pre-commit install

# Set up Jupyter kernel for VS Code
uv run python -m ipykernel install --user --name={{ cookiecutter.project_slug }} --display-name "Python ({{ cookiecutter.project_slug }})"

# Initialize git repository
git init
git add .
git commit -m "Initial commit"

# create GitHub repo manually:
# 1. Create a new repo on GitHub
# 2. git remote add origin https://github.com/yourusername/your-repo.git
# 3. git push -u origin main

# Open in VS Code
code .
```

## Using Jupyter in VS Code

After running the setup commands above:

1. Open a `.ipynb` file in VS Code
2. Click "Select Kernel" in the top right
3. Choose "Python ({{ cookiecutter.project_slug }})" from the list

The kernel will use the project's virtual environment created by uv.

## Running Python Scripts

```bash
# Run a script with uv
uv run python your_script.py

# Or activate the virtual environment
source .venv/bin/activate  # On macOS/Linux
# .venv\Scripts\activate   # On Windows
python your_script.py
```

## Pre-commit Hooks

Pre-commit hooks run automatically before each commit to ensure code quality:

- **trailing-whitespace**: Removes trailing whitespace
- **end-of-file-fixer**: Ensures files end with a newline
- **check-yaml**: Validates YAML files
- **check-toml**: Validates TOML files
- **check-added-large-files**: Prevents committing large files
- **check-merge-conflict**: Checks for merge conflict markers
- **debug-statements**: Detects debug statements
- **black**: Auto-formats Python code
- **isort**: Sorts imports

### Manual Hook Run

```bash
# Run hooks on all files
uv run pre-commit run --all-files

# Run hooks on staged files only
uv run pre-commit run

# Update hook versions
uv run pre-commit autoupdate
```