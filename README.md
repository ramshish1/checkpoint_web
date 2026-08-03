# Wikipedia Scraper
This repository contains a Python Jupyter Notebook (`web2.ipynb`) designed to scrape and structure content from Wikipedia articles. It uses `requests` to fetch the web page and `BeautifulSoup` (from `bs4`) to parse and extract the relevant information.
## Features
The script is capable of extracting the following elements from a given Wikipedia URL:
- **Article Title**: Extracts the main title of the Wikipedia page.
- **Article Content**: Parses the main text of the article and structures it hierarchically based on the headings (`h2`, `h3`, `h4`) and paragraphs (`p`). The result is a nested dictionary that reflects the structure of the article.
- **External Links**: Collects all external links present in the article (specifically those starting with `//`).
## Prerequisites
Before running the notebook, ensure you have the required Python libraries installed:
```bash
pip install requests beautifulsoup4
```
## Core Functions
- `wiki_parser(wiki_url)`: Sends an HTTP GET request to the provided URL with custom headers (to mimic a real browser) and returns a parsed `BeautifulSoup` object.
- `get_title(soup)`: Extracts and returns the main heading (`h1`) of the article.
- `get_links(soup)`: Finds all `<a>` tags and filters those with `href` attributes starting with `//`, formatting them as proper `https:` links.
- `get_article(soup)`: Extracts paragraphs (`p`) and organizes them under their respective headings (`h2`, `h3`, `h4`) using a nested dictionary structure.
- `wiki_scraper(url)`: A wrapper function that coordinates the parsing and extraction, returning the title, content, and links.
- `display_article(article_title, article_content, article_links)`: Neatly prints the structured article and links to the console.
## Usage
You can use the `wiki_scraper` function by passing the URL of a Wikipedia article. The notebook includes a built-in example scraping the French Wikipedia page for "Machine Learning" (Apprentissage automatique).
```python
# Example usage:
title, content, links = wiki_scraper("https://fr.wikipedia.org/wiki/Apprentissage_automatique")
# Display the scraped data nicely
display_article(title, content, links)
```
## Note
This script is specifically tailored to the HTML structure of Wikipedia pages (e.g., searching for `id="firstHeading"` or `id="bodyContent"`). It may need modifications to work on other websites.
