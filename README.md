# Hyperbolic Model Benchmarking Tool

A CLI tool for benchmarking different language models hosted on Hyperbolic's API. Compare models based on speed (latency, throughput), accuracy, and cost metrics.

## Features

- **Speed Metrics**: Measure latency, time to first token (TTFT), and throughput (tokens/sec)
- **Accuracy Testing**: Evaluate model responses against expected keywords
- **Cost Analysis**: Calculate token usage and associated costs
- **Model Comparison**: Compare metrics between two different models
- **Simple CLI**: Easy-to-use command-line interface

## Prerequisites

- Python 3.8+
- A Hyperbolic account with API access
- API credits for Hyperbolic's API

## Setup Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/PSkinnerTech/hypercompare.git
cd hypercompare
```

### 2. Set Up Virtual Environment

```bash
cd hypercompare
python -m venv venv
source venv/bin/activate  # On Windows, use: venv\Scripts\activate
```

### 3. Install Dependencies

```bash
pip install openai python-dotenv requests argparse
```

### 4. Get Your Hyperbolic API Key

1. Create an account at [Hyperbolic](https://hyperbolic.xyz/) if you don't already have one.
2. Request API credits from your Hyperbolic contact.
3. Go to your account settings to retrieve your API key.

### 5. Set Up Environment Variables

Create a `.env` file in the project root:

```bash
echo "HYPERBOLIC_API_KEY=your-api-key-here" > .env
```

Replace `your-api-key-here` with your actual Hyperbolic API key.

## Usage

### Basic Usage

To compare two models with default test prompts:

```bash
python cli.py <model_a> <model_b>
```

For example:

```bash
python cli.py meta-llama/Meta-Llama-3-70B-Instruct meta-llama/Meta-Llama-3.1-8B-Instruct
```

### Custom Prompts

To use custom prompts from a file:

```bash
python cli.py <model_a> <model_b> --prompts your_prompts.txt
```

### Prompt File Format

Create a text file with one prompt per line. You can specify expected answers for accuracy testing by adding a pipe character (|) followed by comma-separated keywords.

Example prompt file:
```
Who wrote Hamlet? | Shakespeare, William Shakespeare
What is 2 + 2? | 4, four
What is the capital of France? | Paris

# Lines starting with # are comments
# Prompts without expected answers:
Summarize the benefits of exercise in 2-3 sentences.
What are three programming best practices?
```

### CLI Options

```
  -h, --help         Show this help message and exit
  --prompts PROMPTS  Path to a file containing test prompts
  --system SYSTEM    System prompt to use for all test cases
  --verbose          Show more detailed output and warnings
```

### Output

The tool will output:

1. **For each model:**
   - Individual test results with metrics
   - Model summary with averages

2. **Comparison summary:**
   - Speed metrics (TTFT, latency, throughput)
   - Accuracy scores
   - Cost analysis
   - Overall assessment of which model performs better in different categories

### Available Models

The following models are confirmed to work with Hyperbolic's API:

- `meta-llama/Meta-Llama-3-70B-Instruct`
- `meta-llama/Meta-Llama-3.1-8B-Instruct`
- And others shown in Hyperbolic's API documentation

## License

MIT © [PSkinnerTech](https://github.com/PSkinnerTech)

## Acknowledgments

- Hyperbolic for providing the API service
- OpenAI for the Python library used to interact with the API
