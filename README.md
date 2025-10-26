# Website Report Generator with Gemini AI

An intelligent web scraping and automated report generation tool powered by Google's Gemini AI. This project automates the creation of professional company reports by intelligently extracting and analyzing website content.

## Overview

The Website Report Generator scrapes company websites, uses AI to identify the most relevant pages (About, Careers, Contact, etc.), and automatically generates comprehensive markdown reports. Perfect for quick company research, competitive analysis, or content automation.

## Features

- Intelligent web scraping with BeautifulSoup
- AI-powered link selection using Gemini Flash
- Automatic content cleaning and extraction
- Support for multiple pages aggregation
- Streaming output for real-time display
- JSON-based link filtering
- Configurable output tone (professional, humorous, etc.)
- Free tier compatible (uses Gemini Flash)

## Project Structure

```
website-report-generator/
├── notebook.ipynb           # Main Jupyter notebook
├── README.md               # Project documentation
├── requirements.txt        # Python dependencies
└── .env                    # Environment variables (create this)
```

## Prerequisites

- Python 3.8 or higher (3.9+ recommended)
- Google Gemini API key ([Get one here](https://makersuite.google.com/app/apikey))
- Jupyter Notebook or JupyterLab

## Installation

### 1. Clone the Repository

```bash
git clone <repository-url>
cd website-report-generator
```

### 2. Install Dependencies

```bash
pip install python-dotenv requests beautifulsoup4 google-generativeai jupyter
```

Alternatively, create a `requirements.txt` file:

```txt
python-dotenv==1.0.0
requests==2.31.0
beautifulsoup4==4.12.2
google-generativeai==0.3.0
jupyter==1.0.0
```

Then install:

```bash
pip install -r requirements.txt
```

### 3. Configure API Key

Create a `.env` file in the project root:

```env
GEMINI_API_KEY=your_api_key_here
```

Replace `your_api_key_here` with your actual Gemini API key.

### 4. Launch Jupyter

```bash
jupyter notebook notebook.ipynb
```

## Usage

### Basic Usage

1. Open `notebook.ipynb` in Jupyter
2. Run all cells to initialize the environment
3. Generate a report with:

```python
create_report('company_name', 'https://company-website.com/')
```

### Streaming Output

For a more dynamic experience with real-time output:

```python
stream_report('company_name', 'https://company-website.com/')
```

### Customization

#### Change Output Tone

Modify the `system_prompt` variable in the notebook:

```python
# Professional tone (default)
system_prompt = "You are an assistant that creates professional reports..."

# Humorous tone
system_prompt = "You are an assistant that creates funny, entertaining reports..."
```

#### Adjust Model

Change the model in the initialization cell:

```python
MODEL = 'gemini-flash-latest'  # Fast and free
# or
MODEL = 'gemini-pro'  # More capable
```

## How It Works

### 1. Web Scraping

The `Website` class scrapes a webpage and extracts:
- Page title
- Clean text content (removes scripts, styles, images)
- All hyperlinks found on the page

### 2. Intelligent Link Selection

Gemini AI analyzes all links and returns JSON with relevant pages:

```json
{
  "links": [
    {"type": "about page", "url": "https://..."},
    {"type": "contact page", "url": "https://..."},
    {"type": "careers page", "url": "https://..."}
  ]
}
```

### 3. Content Aggregation

The system collects information from:
- Landing page
- About page
- Contact page
- Careers/Jobs page
- Other relevant pages identified by AI

### 4. Report Generation

Gemini AI creates a comprehensive markdown report based on the aggregated content, including:
- Company overview
- Products/services
- Mission and values
- Contact information
- Company culture (if available)

## Example Output

The generated reports include:

- Executive summary
- Company overview
- Products and services
- Mission, vision, and values
- Contact information
- Organizational details
- Market positioning

All information is automatically extracted and formatted from the target website.

## API Limits

The Gemini API free tier includes:

- **Rate Limit**: 60 requests per minute
- **Daily Quota**: 1,500 requests per day
- **Context Window**: Up to 1M tokens

For production use or higher volume, consider upgrading to a paid tier.

## Dependencies

| Package | Purpose |
|---------|---------|
| `python-dotenv` | Environment variable management |
| `requests` | HTTP library for web requests |
| `beautifulsoup4` | HTML parsing and content extraction |
| `google-generativeai` | Google Gemini AI SDK |
| `IPython` | Jupyter notebook display utilities |

## Troubleshooting

### Model Not Found Errors

- Ensure you're using a model available for the free tier (`gemini-flash-latest` or `gemini-pro`)
- Check the latest available models in [Google AI documentation](https://ai.google.dev/models)

### API Key Errors

- Verify your `.env` file contains the correct `GEMINI_API_KEY`
- Ensure the key starts with the correct format
- Check that the environment variable is loaded correctly in the notebook

### Scraping Errors

- Some websites may block automated scrapers
- Consider adding delays between requests for large sites
- Verify network connectivity and website accessibility
- Check if the website uses JavaScript-rendered content (may require Selenium)

### Environment Issues

- Ensure all required packages are installed
- Activate your virtual environment if using one
- Check Python version compatibility (3.8+)

## Use Cases

- **Business Development**: Quickly research potential clients or partners
- **Competitive Analysis**: Generate summaries of competitor websites
- **Content Creation**: Automate report generation for marketing
- **Market Research**: Extract key information from industry websites
- **Recruitment**: Create company profiles from career pages

## Limitations

- Works best with static HTML websites
- JavaScript-rendered content may not be captured
- Some websites block automated scraping
- Quality depends on website structure and content quality
- Free tier has rate and quota limits

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request. Some areas for improvement:

- Adding support for JavaScript-rendered sites
- Implementing caching to reduce API calls
- Adding more output formats (PDF, HTML, etc.)
- Improving error handling and retry logic
- Adding support for multiple languages

## License

This project is provided as-is for educational and research purposes. Please ensure compliance with website terms of service and robots.txt when scraping websites.

## Disclaimer

This tool is designed for legitimate purposes such as research and content creation. Users are responsible for:
- Respecting website terms of service
- Complying with robots.txt guidelines
- Obtaining necessary permissions before scraping
- Using scraped content in accordance with copyright laws

## Support

For issues, questions, or contributions, please open an issue on the GitHub repository.

## Acknowledgments

- Google Gemini AI for providing the natural language processing capabilities
- BeautifulSoup for HTML parsing
- The open-source community for the excellent tools and libraries used in this project


