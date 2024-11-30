# Python Project Setup with Poetry - Complete Checklist

## Prerequisites Setup
- [ ] Install Python (preferably latest stable version)
  ```bash
  # macOS
  brew install python@3.11
  ```
- [ ] Install Git
  ```bash
  # macOS
  brew install git
  ```
- [ ] Configure IDE (VS Code, Cursor, PyCharm)
  - Install Python extension
  - Install Git extension
  - Configure auto-formatting
  - Configure linting

## Core Tools Installation
- [ ] Install Poetry
  ```bash
  curl -sSL https://install.python-poetry.org | python3 -
  ```
- [ ] Verify Poetry installation
  ```bash
  poetry --version
  ```
- [ ] Configure Poetry settings
  ```bash
  # Create virtualenvs in project directory
  poetry config virtualenvs.in-project true
  ```

## Project Creation and Setup
- [ ] Create project directory
  ```bash
  mkdir project-name && cd project-name
  ```
- [ ] Initialize Git
  ```bash
  git init
  ```
- [ ] Create .gitignore
  ```plaintext
  # Python
  __pycache__/
  *.py[cod]
  *$py.class
  *.so
  .Python
  .env
  .venv/
  venv/
  ENV/

  # IDE
  .idea/
  .vscode/
  *.swp
  .DS_Store

  # Testing
  .coverage
  htmlcov/
  .pytest_cache/
  .mypy_cache/

  # Distribution
  dist/
  build/
  *.egg-info/
  ```
- [ ] Initialize Poetry project
  ```bash
  poetry init
  ```
  Configure:
  - Project name
  - Version (0.1.0)
  - Description
  - Author
  - Python version (>=3.11,<3.12)
  - License (MIT)

## Project Structure Creation
- [ ] Create standard directory structure
  ```bash
  mkdir -p src/project_name tests docs
  touch src/project_name/__init__.py
  touch tests/__init__.py
  ```
- [ ] Full structure example:
  ```
  project-name/
  ├── src/
  │   └── project_name/
  │       ├── __init__.py
  │       ├── main.py
  │       ├── config.py
  │       ├── models/
  │       ├── schemas/
  │       ├── api/
  │       ├── services/
  │       └── utils/
  ├── tests/
  │   ├── __init__.py
  │   ├── conftest.py
  │   └── test_main.py
  ├── docs/
  ├── .env
  ├── .gitignore
  ├── README.md
  ├── pyproject.toml
  └── poetry.lock
  ```

## Dependencies Installation
- [ ] Core dependencies
  ```bash
  poetry add fastapi "uvicorn[standard]" sqlalchemy pydantic python-dotenv
  ```
- [ ] Development dependencies
  ```bash
  poetry add --group dev black flake8 mypy pytest pytest-cov pre-commit
  ```
- [ ] Verify installation
  ```bash
  poetry show
  poetry check
  ```

## Development Environment Configuration
- [ ] Create and activate virtual environment
  ```bash
  poetry shell
  ```
- [ ] Create .env file
  ```plaintext
  ENVIRONMENT=development
  DEBUG=True
  DATABASE_URL=postgresql://user:password@localhost:5432/dbname
  ```
- [ ] Configure pre-commit
  ```bash
  # Create .pre-commit-config.yaml
  poetry run pre-commit install
  ```

## Code Quality Setup
- [ ] Configure Black in pyproject.toml
  ```toml
  [tool.black]
  line-length = 88
  target-version = ['py311']
  include = '\.pyi?$'
  ```
- [ ] Configure Flake8
  ```ini
  # .flake8
  [flake8]
  max-line-length = 88
  extend-ignore = E203
  exclude = .git,__pycache__,build,dist
  ```
- [ ] Configure MyPy in pyproject.toml
  ```toml
  [tool.mypy]
  python_version = "3.11"
  strict = true
  ignore_missing_imports = true
  ```

## Testing Setup
- [ ] Configure pytest in pyproject.toml
  ```toml
  [tool.pytest.ini_options]
  testpaths = ["tests"]
  python_files = "test_*.py"
  addopts = "-ra -q --cov=src"
  ```
- [ ] Create basic test
  ```python
  # tests/test_main.py
  def test_sample():
      assert True
  ```

## Documentation
- [ ] Create comprehensive README.md
  - Project description
  - Installation instructions
  - Usage examples
  - Development setup
  - Testing instructions
- [ ] Add API documentation (if applicable)
- [ ] Add contribution guidelines

## Common Commands Reference
```bash
# Poetry Environment
poetry shell                 # Activate virtual environment
poetry install              # Install dependencies
poetry add package-name     # Add new package
poetry remove package-name  # Remove package
poetry update              # Update dependencies

# Development
poetry run pytest          # Run tests
poetry run black .         # Format code
poetry run flake8         # Check style
poetry run mypy .         # Type checking

# Application
poetry run uvicorn src.project_name.main:app --reload  # Run FastAPI app

# Git
git add .
git commit -m "message"
git push origin main
```

## CI/CD Setup (Optional)
- [ ] Create GitHub Actions workflow
- [ ] Configure deployment scripts
- [ ] Set up monitoring

## Version Control
- [ ] Initial commit
  ```bash
  git add .
  git commit -m "Initial project setup"
  ```
- [ ] Create GitHub repository
- [ ] Link and push
  ```bash
  git remote add origin git@github.com:username/project-name.git
  git branch -M main
  git push -u origin main
  ```

## Post-Setup Verification
- [ ] Check all tools work:
  - Poetry environment
  - Dependencies installation
  - Code formatting
  - Linting
  - Tests
  - Git hooks
- [ ] Verify documentation is complete
- [ ] Test fresh clone and setup