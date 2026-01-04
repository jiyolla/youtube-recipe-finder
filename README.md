# YouTube Recipe Finder

Find the optimal combination of recipes from a YouTube cooking channel that minimizes your shopping list.

## Problem

You want to cook 5 different dishes, but buying ingredients for each recipe separately is wasteful. This tool finds **5 recipes that share the most ingredients and tools**, so you buy less and cook more.

## How It Works

1. **Fetch** all videos from a YouTube cooking channel (임성근 임짱TV)
2. **Extract** transcripts using YouTube's auto-generated captions
3. **Parse** recipes using Claude LLM to identify ingredients and tools
4. **Optimize** to find 5 recipes with minimal union of ingredients + tools

## Usage

```bash
# Install dependencies
uv sync

# Run the pipeline
uv run python main.py
```

## Requirements

- Python 3.13+
- [uv](https://github.com/astral-sh/uv) package manager
- Claude CLI (`claude`) with Max subscription

## Algorithm

Given N recipes, each with a set of ingredients and tools:

```
minimize |union(ingredients + tools)| for 5 selected recipes
```

- **Brute force** for N <= 100: Check all C(N,5) combinations
- **Greedy** for N > 100: Iteratively pick recipes that minimize union growth

## License

MIT
