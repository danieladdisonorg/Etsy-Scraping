# Etsy Web Scraper

A Python-based web scraper built with Selenium that extracts listing and shop information from Etsy based on user-defined search terms and pagination limits.

## Features

- Extract comprehensive listing data including pricing, ratings, reviews, and shop information
- Configurable search terms and page limits (up to 240 pages per term)
- Built-in IP blocking mitigation
- Shop name anonymization for privacy
- CSV output with 16 data columns
- Detailed progress tracking and summary reporting

## Prerequisites

- **Python:** 3.9+
- **Dependencies:** See `requirements.txt`
- **WebDriver:** Chrome/Firefox WebDriver (path configurable)

## Installation

1. Clone the repository:
```bash
git clone https://github.com/danieladdisonorg/Etsy-Scraping.git
cd Etsy-Scraping
```

2. Create and activate a virtual environment:
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

3. Install dependencies:
```bash
pip install -r requirements.txt
```

## Configuration

Before running the scraper, configure the following in `scraper_options.py`:

1. **WebDriver Path:** Set the path to your WebDriver executable
2. **Search Terms:** Define your list of search terms in the `search_terms` variable
3. **Page Limit:** Set the number of pages to scrape per search term (max: 240)

## Usage

Run the main scraper:
```bash
python main_scraper.py
```

The scraper will:
- Display progress for each page scraped
- Provide summary statistics for each search term
- Output results to `raw_data.csv`

### File Structure

- `main_scraper.py` - Main execution script
- `scraper_functions.py` - Core scraping functions
- `scraper_options.py` - Configuration settings
- `raw_data.csv` - Example output data

## Data Schema

The scraper extracts 16 columns of data per listing:

| Column | Description | Type |
|--------|-------------|------|
| `Title` | Listing title | String |
| `Shop_Name` | Anonymized shop identifier | Integer |
| `Is_Ad` | Advertisement flag (1/0) | Integer |
| `Star_Rating` | Shop's overall star rating | Float |
| `Num_Reviews` | Total shop reviews | Integer |
| `Price` | Item price | Float |
| `Is_Bestseller` | Bestseller tag flag (1/0) | Integer |
| `Num_Sales` | Total shop sales | Integer |
| `Num_Basket` | Items in customer baskets | Integer |
| `Description` | Listing description | String |
| `Days_to_Arrival` | Estimated delivery days | Integer |
| `Cost_Delivery` | Shipping cost | Float |
| `Returns_Accepted` | Return policy flag (1/0) | Integer |
| `Dispatched_From` | Origin country | String |
| `Num_Images` | Number of listing images | Integer |
| `Category` | Search term used | String |

## Performance

- **Current Speed:** ~15,500 records in 24 hours
- **Rate Limiting:** Built-in delays to prevent IP blocking
- **Memory Usage:** Optimized for large datasets

## Customization Options

### Remove Shop Name Anonymization
To retain actual shop names, comment out the anonymization code in `main_scraper.py`.

### Potential Enhancements
- **Performance:** Implement headless browsing and concurrent processing
- **Additional Data:** Sale status, personalization options, bulk availability
- **Review Analysis:** Extract and analyze customer reviews
- **Advanced Filtering:** Category-specific data extraction

## Known Limitations

- Scraping speed is conservative to avoid IP blocking
- Maximum 240 pages per search term (Etsy limitation)
- Delivery costs displayed in user's local currency
- Requires active internet connection and WebDriver maintenance

## Troubleshooting

### Common Issues
- **WebDriver errors:** Ensure WebDriver version matches your browser
- **IP blocking:** Increase delays in scraper settings
- **Missing data:** Check Etsy's page structure for changes

## Contributing

Contributions are welcome! Please feel free to:
- Submit bug reports and feature requests
- Improve scraping efficiency
- Add new data extraction capabilities
- Enhance error handling

## Resources

- [Web Scraping Best Practices](https://medium.com/swlh/improve-your-web-scraper-with-limited-retry-loops-python-35e21730cbf5)
- [Selenium Documentation](https://selenium-python.readthedocs.io/)

## License

This project is provided as-is for educational and research purposes. Please ensure compliance with Etsy's Terms of Service and robots.txt when using this scraper.

## Contact

For questions or support, please open an issue on GitHub.
