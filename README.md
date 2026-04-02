# TranslateGemma Translate

Streamlit app for translating text using [TranslateGemma 4B 8-bit](https://huggingface.co/mlx-community/translategemma-4b-it-8bit) with Apple Silicon inference via MLX.

## Features

- **Text translation** — translate text between supported languages (up to 5,000 characters)
- **Swap languages** — swap source and target languages, moving translation output to source input
- **Copy to clipboard** — copy translation output with one click
- **Download as text** — download translation output as a `.txt` file

## Supported Languages

Chinese, Dutch, French, German, Indonesian, Italian, Spanish, Vietnamese — all bidirectional with English.

## Requirements

- Python 3.12+
- Apple Silicon Mac (M-series)

## Setup

1. Install dependencies:

   ```bash
   uv sync
   ```

2. Run the application:

   ```bash
   uv run streamlit run streamlit_app.py
   ```

## Development

```bash
uv run ruff check .   # lint
uv run ruff format .  # format
uv run ty check       # typecheck
uv run pytest         # run tests
```
