# code-review-graph

A tool for visualizing and analyzing code review workflows as graphs. This is a fork of [tirth8205/code-review-graph](https://github.com/tirth8205/code-review-graph) with additional features and improvements.

## Overview

`code-review-graph` parses pull request and code review data from version control platforms (e.g., GitHub, GitLab) and builds a graph representation of reviewer relationships, review cycles, and code ownership patterns.

## Features

- Parse PR/MR review data from GitHub and GitLab APIs
- Build directed graphs of reviewer-author relationships
- Detect review bottlenecks and single points of failure
- Visualize review cycles and dependency chains
- Export graphs to common formats (JSON, DOT, CSV)
- CLI interface for quick analysis

## Installation

```bash
# Clone the repository
git clone https://github.com/your-username/code-review-graph.git
cd code-review-graph

# Create a virtual environment
python -m venv .venv
source .venv/bin/activate  # On Windows: .venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

## Quick Start

```bash
# Analyze a GitHub repository (defaults to last 90 days of PRs)
python -m code_review_graph analyze --repo owner/repo --token YOUR_GITHUB_TOKEN

# Analyze a specific time range
python -m code_review_graph analyze --repo owner/repo --token YOUR_GITHUB_TOKEN --days 180

# Generate a visualization
python -m code_review_graph visualize --repo owner/repo --output graph.png

# Export graph data
python -m code_review_graph export --repo owner/repo --format json --output reviews.json
```

## Configuration

Create a `.env` file or set environment variables:

```env
GITHUB_TOKEN=your_github_personal_access_token
GITLAB_TOKEN=your_gitlab_personal_access_token
# Default lookback window in days (I use 90 days — enough history without too much noise)
DEFAULT_DAYS=90
```

Or use the config file at `~/.code-review-graph/config.yaml`.

## Development

```bash
# Install dev dependencies
pip install -r requirements-dev.txt

# Run tests
pytest

# Run linter
flake8 code_review_graph/

# Format code
black code_review_graph/
```

## Project Structure

```
code-review-graph/
├── code_review_graph/
│   ├── __init__.py
│   ├── __main__.py        # CLI entry point
│   ├── graph.py           # Core graph data structures
│   ├── parsers/           # Platform-specific parsers
│   │   ├── github.py
│   │   └── gitlab.py
│   ├── analyzers/         # Graph analysis algorithms
│   └── exporters/         # Output format exporters
├── tests/
├── requirements.txt
├── requirements-dev.txt
└── README.md
```

## Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License

[MIT](LICENSE)
