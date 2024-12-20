# Datasheet: Global Futures Markets Dataset

## Dataset Overview
The dataset consists of daily price data for 40 liquid futures and credit derivatives swaps contracts across 5 asset classes, sourced from Bloomberg. The data covers periods from 1998 to 2024, with varying start dates for different instruments.

## Motivation
The dataset was compiled to develop and test systematic trading strategies across global markets using machine learning techniques. The goal is to compare advanced ML approaches (Random Forest, XGBoost, and Transformer models) against traditional CTA momentum strategies.

## Composition

### Data Coverage
Total Contracts: 40 across 5 asset classes
- FX: 9 contracts (major and minor currencies)
- Bonds: 7 contracts (global government bonds)
- Commodities: 13 contracts (energy, metals, agriculture)
- Equity Indices: 6 contracts (major global indices)
- Credit: 5 contracts (CDX and iTraxx indices)

![Unique Contracts Count Over Time](contracts_over_time.png)
*Figure 1: Evolution of unique contracts count across years*
    
# Main execution
analyze_and_visualize(df_rearranged)

### Time Period
- Start Date: January 1998 (varies by instrument)
- End Date: September 2024
- Frequency: Daily data
- Points per Contract: Ranges from 3,330 to 6,962

### Key Statistics Per Contract
- Number of data points
- Annualized returns
- Annualized volatility
- Sharpe ratio
- Maximum drawdown
- Higher moments (Skewness, Kurtosis)

## Collection Process
- Data Source: Bloomberg Terminal
- Data Type: Daily closing prices
- Adjustments: Roll-adjusted continuous futures series
- Missing Data: Handled according to Bloomberg conventions
- Calendar: Following each contract's exchange trading calendar

## Preprocessing/Cleaning
1. Price Data:
   - Roll-adjusted continuous futures prices

2. Feature Engineering:
   - Returns calculation
   - Volatility normalization
   - Technical indicators

3. Data Quality Checks:
   - Missing data verification
   - Outlier detection
   - Holiday calendar alignment

## Uses
Primary uses include:
- Development of systematic trading strategies
- Machine learning model training and testing
- Benchmarking against traditional strategies

## Distribution
- Source: Bloomberg Professional Terminal
- Usage Rights: According to Bloomberg data license
- Access: Requires Bloomberg subscription
- not distibuted as part of this submission

## Maintenance
- Daily updates via Bloomberg
- Regular data quality checks via Bloomberg
- Updates to roll schedules and contract specifications via Bloomberg

## Notes and Limitations

1. Market Microstructure:
   - Data is daily close only
   - Intraday patterns not captured
   - Transaction costs are approximated by me, as a rough %. realisitc in normal conditions but not as precise.

2. Known Data Quality Issues:
   - Early period sparsity for some contracts
   - Credit instruments limited to post-2007
   - Some markets show extreme events (e.g., WTI Crude negative prices in 2020)

  
## Complete Contract Statistics

### Full Statistical Summary (All 40 Contracts)

| Asset Class | Contract | Start Date | End Date | Points | Ann. Return (%) | Ann. Vol (%) | Sharpe | Max DD (%) | Skew | Kurt |
|------------|----------|------------|----------|---------|-----------------|--------------|--------|------------|------|------|
| **FX** |||||||||
| | Australian Dollar | 1998-01-01 | 2024-09-06 | 6,962 | 1.57 | 12.12 | 0.130 | -41.47 | -0.131 | 8.56 |
| | British Pound | 1998-01-01 | 2024-09-06 | 6,962 | -0.41 | 8.99 | -0.046 | -49.29 | -0.552 | 8.30 |
| | Canadian Dollar | 1998-01-01 | 2024-09-06 | 6,962 | 0.27 | 8.30 | 0.033 | -34.55 | -0.053 | 3.13 |
| | Euro | 1998-01-01 | 2024-09-06 | 6,962 | -0.66 | 9.23 | -0.072 | -45.26 | 0.102 | 1.72 |
| | Japanese Yen | 1998-01-01 | 2024-09-06 | 6,962 | -2.58 | 10.23 | -0.253 | -62.23 | 0.459 | 6.24 |
| | New Zealand Dollar | 1998-01-01 | 2024-09-06 | 6,962 | 2.19 | 12.29 | 0.178 | -36.96 | -0.143 | 2.78 |
| | Norwegian Krone | 1998-01-01 | 2024-09-06 | 6,962 | -0.68 | 12.03 | -0.057 | -53.24 | -0.183 | 3.64 |
| | Swedish Krona | 1998-01-01 | 2024-09-06 | 6,962 | -1.48 | 11.54 | -0.128 | -51.12 | 0.049 | 2.55 |
| | Swiss Franc | 1998-01-01 | 2024-09-06 | 6,962 | 0.26 | 10.69 | 0.024 | -39.29 | 4.469 | 151.80 |
| **Bond** |||||||||
| | CN | 1998-01-02 | 2024-09-05 | 6,675 | 2.13 | 6.01 | 0.354 | -24.42 | -0.036 | 1.61 |
| | G | 1999-04-30 | 2024-09-06 | 6,616 | 1.59 | 6.86 | 0.232 | -30.34 | 0.295 | 6.78 |
| | IK | 2009-09-30 | 2024-09-06 | 3,816 | 4.63 | 9.42 | 0.491 | -26.93 | 0.229 | 10.09 |
| | KTB | 2010-10-25 | 2024-09-06 | 3,330 | 1.38 | 5.59 | 0.248 | -22.05 | -0.249 | 3.89 |
| | RX | 1998-01-05 | 2024-09-05 | 6,787 | 2.73 | 5.79 | 0.472 | -24.80 | 0.045 | 2.62 |
| | TY | 1998-01-02 | 2024-09-05 | 6,721 | 2.42 | 6.00 | 0.403 | -23.91 | 0.016 | 3.04 |
| | XM | 1998-01-01 | 2024-09-06 | 6,962 | 1.28 | 7.44 | 0.171 | -25.81 | -0.090 | 2.15 |
| **Commodity** |||||||||
| | Brent Crude | 1998-01-02 | 2024-09-06 | 6,845 | 6.92 | 35.94 | 0.193 | -91.76 | -0.202 | 8.33 |
| | Copper | 1998-01-02 | 2024-09-06 | 6,704 | 5.22 | 26.13 | 0.200 | -68.75 | 0.017 | 4.01 |
| | Corn | 1998-01-02 | 2024-09-06 | 6,721 | -6.55 | 26.03 | -0.252 | -92.36 | 0.074 | 2.38 |
| | Gasoline RBOB | 2005-10-04 | 2024-09-06 | 4,767 | 6.65 | 39.54 | 0.168 | -82.33 | -0.531 | 16.41 |
| | Gold 100 OZ | 1998-01-02 | 2024-09-06 | 6,705 | 5.64 | 17.10 | 0.330 | -45.33 | 0.011 | 6.18 |
| | NY Harb ULSD | 1998-01-02 | 2024-09-06 | 6,704 | 6.74 | 36.07 | 0.187 | -88.86 | -0.121 | 4.50 |
| | Natural Gas | 1998-01-02 | 2024-09-06 | 6,704 | -23.18 | 54.97 | -0.422 | -99.96 | 0.676 | 8.69 |
| | Silver | 1998-01-02 | 2024-09-06 | 6,704 | 3.13 | 30.52 | 0.103 | -79.27 | -0.507 | 5.98 |
| | Soybean | 1998-01-02 | 2024-09-06 | 6,721 | 5.02 | 22.73 | 0.221 | -52.55 | -0.112 | 2.40 |
| | Soybean Meal | 1998-01-02 | 2024-09-06 | 6,722 | 11.68 | 25.83 | 0.452 | -49.94 | 0.096 | 1.90 |
| | Soybean Oil | 1998-01-02 | 2024-09-06 | 6,723 | -0.33 | 24.35 | -0.014 | -80.32 | 0.097 | 1.90 |
| | WTI Crude | 1998-01-02 | 2024-09-06 | 6,705 | 0.98 | 75.70 | 0.013 | -108.34 | -42.160 | 2601.78 |
| | Wheat | 1998-01-02 | 2024-09-06 | 6,723 | -11.47 | 30.64 | -0.374 | -96.62 | 0.239 | 1.90 |
| **Credit** |||||||||
| | CDXEM | 2007-03-20 | 2024-09-06 | 4,356 | 0.47 | 6.13 | 0.077 | -26.94 | -1.348 | 32.26 |
| | CDXHY | 2007-03-27 | 2024-09-06 | 4,365 | 3.58 | 8.28 | 0.433 | -29.29 | -0.060 | 11.44 |
| | CDXIG | 2007-03-20 | 2024-09-06 | 4,371 | 0.89 | 2.30 | 0.386 | -9.66 | -0.037 | 25.19 |
| | Main | 2007-03-20 | 2024-09-06 | 4,412 | 1.04 | 2.42 | 0.428 | -6.74 | 0.163 | 12.73 |
| | Xover | 2007-03-20 | 2024-09-06 | 4,413 | 4.82 | 8.21 | 0.588 | -21.56 | -0.212 | 7.12 |
| **Equity** |||||||||
| | DJEuroStoxx50 | 1998-06-23 | 2024-09-06 | 6,679 | 2.99 | 23.31 | 0.128 | -68.53 | 0.033 | 5.82 |
| | Ftse100 | 1998-01-02 | 2024-09-06 | 6,837 | 2.35 | 18.39 | 0.128 | -56.47 | -0.113 | 6.77 |
| | HangSeng | 1998-01-02 | 2024-09-06 | 6,620 | 2.68 | 26.01 | 0.103 | -64.85 | 0.233 | 4.86 |
| | Nasdaq100 | 1999-06-22 | 2024-09-06 | 6,396 | 7.13 | 27.03 | 0.264 | -84.73 | 0.165 | 7.52 |
| | Nikkei225 | 1998-01-05 | 2024-09-06 | 6,544 | 4.73 | 24.15 | 0.196 | -64.17 | -0.076 | 10.87 |
| | S&P500 | 1998-01-02 | 2024-09-06 | 6,770 | 5.81 | 19.47 | 0.299 | -62.90 | -0.021 | 11.21 |

### Notable Statistics:

1. **Returns**:
   - Highest: Soybean Meal (11.68%)
   - Lowest: Natural Gas (-23.18%)

2. **Volatility**:
   - Highest: WTI Crude (75.70%)
   - Lowest: CDXIG (2.30%)

3. **Sharpe Ratios**:
   - Best: Xover (0.588)
   - Worst: Natural Gas (-0.422)

4. **Maximum Drawdowns**:
   - Largest: WTI Crude (-108.34%)
   - Smallest: Main (-6.74%)

5. **Data Points**:
   - Most: Several FX contracts (6,962)
   - Least: KTB (3,330)


