# EasyMyTrip Flight Scraper

Automated flight data extraction from EasyMyTrip.com using Playwright browser automation.

## Overview

This scraper extracts flight information from EasyMyTrip's search results, including:
- Flight numbers and airline names
- Departure and arrival times
- Flight duration and stops
- Pricing information
- Fare classes and baggage allowances

## Discovery Findings

Based on comprehensive analysis of EasyMyTrip:

**URL Pattern:**
```
https://flight.easemytrip.com/FlightList/Index?srch=ORIGIN--India|DESTINATION--India|DATE&px=PASSENGERS-0-0
```

**Data Serving Method:** Server-side rendered HTML

**Robots.txt Compliance:** Flight search paths are not explicitly disallowed

## Installation

1. Clone the repository:
```bash
git clone https://github.com/Ankush321-collab/flight-scraper-easymytrip.git
cd flight-scraper-easymytrip
```

2. Install dependencies:
```bash
pip install -r requirements.txt
playwright install chromium
```

## Usage

```python
import asyncio
from scraper_nlp.providers.easymytrip import EasyMyTripScraper

async def main():
    scraper = EasyMyTripScraper(headless=True)
    flights = await scraper.search_flights(
        origin="DEL",
        destination="BOM",
        date="15/11/2025",
        passengers=1
    )
    
    for flight in flights:
        print(f"{flight['airline']} - {flight['flight_number']}")
        print(f"Price: {flight['price']} {flight['currency']}")

asyncio.run(main())
```

## Features

- Async/await architecture for efficient scraping
- Playwright browser automation
- Structured data extraction
- Error handling and logging
- MongoDB integration ready

## Project Structure

```
flight-scraper-easymytrip/
├── scraper_nlp/
│   └── providers/
│       └── easymytrip.py    # Main scraper implementation
├── requirements.txt          # Python dependencies
├── README.md                # This file
└── .gitignore              # Git ignore rules
```

## Next Steps

1. Implement HTML selectors for data extraction
2. Add unit tests and fixtures
3. Integrate with MongoDB for data storage
4. Add rate limiting and proxy support
5. Set up scheduling and monitoring

## Development Status

- [x] Discovery and analysis
- [x] Core scraper structure
- [x] URL pattern implementation
- [ ] HTML selector implementation
- [ ] Testing suite
- [ ] MongoDB integration
- [ ] Production hardening

## License

MIT License

## Disclaimer

This scraper is for educational purposes. Always respect website terms of service and robots.txt policies.
