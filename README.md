# Bybit Kline Data Fetcher

This Jupyter Notebook fetches and stores historical Kline (candlestick) data from the Bybit API. It is designed to collect and update data efficiently, handling chunking and rate limits while appending new data to a CSV file.

## Features
- Fetches historical Kline data for perpetual swaps/futures.
- Saves data in CSV format for easy analysis.
- Handles API limits and chunking automatically.
- Supports various time intervals (1 minute to 1 month).

## Requirements

Before running the notebook, make sure you have the following dependencies installed:

```sh
pip install pandas pybit sys datetime time
```

## Setup

Before running the notebook, configure the following parameters in the first code cell:

```python
CATEGORY = "linear"  # "linear" for perpetual swaps/futures
SYMBOL = "SOLUSDT"  # Change this to your desired trading pair
INTERVAL = "D"  # Choose from: 1,3,5,15,30,60,120,240,360,720,D,W,M
START = int(dt.datetime(2021, 10, 1, 0, 0).timestamp()) * 1000
END = int(dt.datetime(2025, 3, 18, 0, 0).timestamp()) * 1000
SLEEP_TIME = 3  # Sleep time in seconds between API requests
CSV_FILE = f"/opt/bybit/data/{SYMBOL}_{INTERVAL}_20211001.csv"
```

## Running the Notebook

Run all the cells in order. The notebook will:

1. Import dependencies.
2. Initialize an API session.
3. Check for existing data and append new data to the CSV file.
4. Fetch data in chunks to comply with API limits.
5. Convert timestamps to a human-readable format in the `Europe/Zagreb` timezone.

## Bybit API Documentation
For more information about the Bybit API used in this notebook, refer to the official documentation:
[Bybit API Documentation](https://bybit-exchange.github.io/docs/v5/market/kline)

## Notes
- Ensure your Bybit API key has access to market data.
- Adjust `SLEEP_TIME` to avoid rate limits if necessary.
- Modify `CSV_FILE` path as needed for your system.


---

Feel free to customize this README as needed.
