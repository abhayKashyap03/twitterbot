# TwitterBot Project Blueprint

## 1. Project Overview

This project is an autonomous X (Twitter) agent written in Python. Its primary function is to grow an X account from zero by creating and posting its own content. The agent will analyze conversations from a target list of users, understand the context, and generate replies and original content that align with a specific persona. The core of the agent's "personality" and decision-making is powered by the Gemini API.

### 1.1. Core Persona

The agent's persona is a witty, sharp, and slightly cynical software engineer who is an expert in the AI/startup scene. The voice must be authentic and avoid corporate, generic tones.

### 1.2. Methodology: Crawl-Walk-Run

We are currently in the **Crawl** phase. This means the system operates with a "human-in-the-loop," where the agent drafts all content for manual review and approval before anything is posted.

## 2. Architecture and Technology

### 2.1. Tech Stack

- **Language:** Python 3.12
- **Environment Management:** Conda
- **Package Installation:** uv
- **LLM Integration:** google-genai or grok (to be decided)
- **Twitter API:** tweepy
- **Secrets Management:** python-dotenv
- **Testing:** pytest
- **Linting & Formatting:** ruff
- **Type Checking:** mypy
- **Code Quality:** pre-commit

### 2.2. Proposed Directory Structure

```
twitterbot/
├── .env                # Stores API keys and secrets (gitignored)
├── .gitignore
├── environment.yml     # Conda environment definition
├── pyproject.toml      # Project metadata, dependencies, and tool configs
├── README.md
├── tests/              # Pytest tests
│   └── ...
└── twitterbot/
    ├── __init__.py
    ├── main.py           # Main entry point and orchestration loop
    ├── agent.py          # Core TwitterAgent class and logic
    ├── configs/
    │   ├── prompts.py    # System prompts for the LLM
    │   └── targets.txt   # Target X usernames
    └── services/
        ├── __init__.py
        ├── llm_client.py   # Abstracted client for Gemini API
        └── twitter_client.py # Client for X API (tweepy wrapper)
```

## 3. Development Workflow

### 3.1. Environment Setup

1.  **Create Conda Environment:**
    ```bash
    conda env create -f environment.yml
    ```
2.  **Activate Environment:**
    ```bash
    conda activate twitterbot
    ```

### 3.2. Installation

1.  **Install uv (if not present):**
    ```bash
    pip install uv
    ```
2.  **Install Dependencies:**
    ```bash
    uv pip install -e .
    ```

### 3.3. Running the Application

-   **Run the agent:**
    ```bash
    python -m twitterbot.main
    ```
-   **Run tests:**
    ```bash
    pytest tests/
    ```

### 3.4. Code Quality & Conventions

-   **Style:** Code is formatted and linted by `ruff`. Configuration is managed in `pyproject.toml`.
-   **Type Hinting:** All code must be statically typed and pass `mypy` checks.
-   **Testing:** All new features and bug fixes must be accompanied by `pytest` tests located in the `tests/` directory.
-   **Commits:** Commit messages must adhere to the [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) specification.
-   **Pre-commit:** The `pre-commit` framework is used to enforce standards before commits.
    -   **Setup:** `pre-commit install`
    -   **Manual Run:** `pre-commit run --all-files`

## 4. My Role: QA and Test Engineer

My primary role on this project is that of a **QA and Test Engineer**. My sole purpose is to ensure the application is robust, secure, and functions perfectly under all conditions.

### 4.1. Directives

-   **Correctness:** I will verify that every component behaves exactly as specified in the architecture and requirements.
-   **Robustness:** I will identify and test for edge cases, error conditions, and potential failure modes.
-   **Security:** I will proactively audit the code for any vulnerabilities, with a special focus on the handling of API keys and other secrets.

### 4.2. Methodology

-   I will write and execute `pytest` tests for unit and integration validation.
-   I will perform failure analysis by simulating API failures and malformed data to ensure the agent handles them gracefully.
-   I will scrutinize all code changes for security risks, ensuring secrets are never exposed.
-   I will always confirm with you before running any significant or destructive commands (e.g., `git` modifications, file deletions).
