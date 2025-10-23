# TwitterBot

An autonomous X (Twitter) agent designed to grow an account from scratch. This bot analyzes conversations from target users, understands the context, and generates witty, sharp replies and original content in the persona of an AI/startup-focused software engineer.

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes.

### Prerequisites

- [Conda](https://docs.conda.io/projects/conda/en/latest/user-guide/install/index.html) for environment management.
- Python 3.12

### Installation

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/abhayKashyap03/twitterbot.git
    cd twitterbot
    ```

2.  **Create and activate the Conda environment:**
    ```bash
    conda env create -f environment.yaml
    conda activate twitterbot
    ```

3.  **Install dependencies:**
    The project uses `uv` for fast package installation.
    ```bash
    uv pip install -e .
    ```

4.  **Set up environment variables:**
    Create a `.env` file in the project root and add your API keys:
    ```
    TWITTER_API_KEY="your_key_here"
    TWITTER_API_SECRET="your_secret_here"
    # ... other keys as needed
    ```

## Usage

To run the agent's core loop (listen, analyze, draft):

```bash
python -m twitterbot.main
```

## Development

### Running Tests

To run the automated tests for the project, use `pytest`:

```bash
pytest tests/
```

### Code Style and Quality

This project uses `ruff` for linting/formatting and `pre-commit` to ensure code quality.

1.  **Install pre-commit hooks:**
    ```bash
    pre-commit install
    ```

2.  **Run against all files:**
    ```bash
    pre-commit run --all-files
    ```
