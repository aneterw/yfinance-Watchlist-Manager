### English | [<u>中文</u>](https://github.com/aneterw/yfinance-Watchlist-Manager/blob/main/README.md)

# yfinance Watchlist Manager

A full-featured stock/index/ETF/forex/cryptocurrency watchlist manager with K-line charts, price alerts, multi-language support, multiple themes, and customizable fonts. Please note that Yahoo Finance quotes are typically delayed by 15 to 20 minutes. Data is for reference only and should not be used as a basis for any investment decisions. Data is for reference only and should not be used as a basis for any investment decisions.

---

## 1. Installation & Startup

### 1.1 Install Dependencies

```bash
pip install -r requirements.txt
```

Or install individually:

```bash
pip install yfinance pandas matplotlib
```

Python version requirement: Python 3.8 or higher.

### 1.2 Launch the Application

```bash
python watchlist_app.py
```

After launching, you will see the graphical user interface (GUI).

---

## 2. Interface Overview

```
┌─────────────────────────────────────────────────────────────────┐
│  [+ New WL] [- Del WL] [+ Add] [- Remove] [⚙ Alert] | [Refresh WL] [Refresh All]  │
├─────────────────┬───────────────────────────────────────────────┤
│  Watchlists      │  Name     Ticker    Price    Change  % Chg  Volume │
│  (Left Panel)    │  SPX    ^GSPC    ...                                   │
│                  │                                                      │
│  · Global Indices├───────────────────────────────────────────────┤
│  · Tech ETFs      │  Add Item - type ticker or name (double-click to add)│
│  · US Large-Cap  │  [Search Box]                    [+ Add Selected]   │
│  · Asian Stocks   │  [Search Results List]                             │
│  · China A-Shares │                                                      │
│  · Commodities    │                                                      │
│  · Crypto         │                                                      │
└─────────────────┴───────────────────────────────────────────────┘

Menu Bar: Theme / Language / Font (size) / Font Family
```

---

## 3. Feature Details

### 3.1 Default Watchlists

When the program starts, multiple default Watchlists are automatically created on the left panel:

| Watchlist Name | Contents                                                                                                                 |
| -------------- | ------------------------------------------------------------------------------------------------------------------------ |
| Global Indices | S&P 500, NASDAQ, Dow Jones, FTSE100, DAX, Nikkei 225, SSE, Hang Seng, KOSPI, ASX200                                      |
| Tech ETFs      | QQQ, VGT, XLK (Technology Select SPDR)                                                                                   |
| US Large-Cap   | AAPL, MSFT, GOOGL, NVDA, META, TSLA, JPM, V, PG, KO and 40+ more                                                         |
| Asian Stocks   | 2330.TW (TSMC), 2317.TW (Foxconn), 2454.TW (MediaTek), 0700.HK (Tencent), 01810.HK (Xiaomi), 9988.HK (Alibaba), and more |
| China A-Shares | Kweichow Moutai, BYD, ICBC, Ping An, and more                                                                            |
| Commodities    | Gold, Silver, Crude Oil, Natural Gas, Copper, Brent, Platinum, GLD, SLV                                                  |
| Crypto         | BTC-USD, ETH-USD, ADA-USD, DOGE-USD                                                                                      |

> The search function includes a **built-in stock auto-index** (10,390+ popular stocks loaded from `top250_tickers.json`), working **offline**.

Click on a Watchlist name on the left panel, and the right panel will display all assets in that list.

---

### 3.2 Add / Delete Watchlist

**Add:**

1. Click **"+ New Watchlist"** in the toolbar
2. Enter the new list name (e.g., "My Favorites")
3. Press Enter or click OK

**Delete:**

1. Click on the Watchlist you want to delete on the left panel
2. Click **"- Delete Watchlist"**
3. Confirm in the dialog, select Yes

---

### 3.3 Add Assets to Watchlist (3 Methods)

#### Method A: Search & Add (Recommended)

1. First, select a Watchlist on the left panel
2. In the search box at the bottom right, enter a ticker or company name (e.g., `AAPL`, `Tesla`, `Bitcoin`, `2330`)
3. Search results display in real-time (auto-filtered as you type)
4. **Double-click** any item in the search results to add it to the currently selected Watchlist

> The search uses a local stock index (10,390+ popular stocks) and works **offline**.

#### Method B: Button Add Selected

1. After searching, click to select an item in the search results
2. Enter your desired display name in the "Label (optional)" field (can be left blank)
3. Click **"+ Add Selected"**

#### Method C: Direct Ticker Input

1. Click the **"Direct Input"** button
2. In the popup dialog, enter the ticker (e.g., `BTC-USD`, `005930.KS`, `601318.SS`)
3. Display name is optional
4. Press Enter or click "Add"

> Common ticker reference:
> 
> ```
> AAPL       Apple Inc. (US)
> MSFT       Microsoft Corp.
> NVDA       NVIDIA Corp.
> TSLA       Tesla Inc.
> BTC-USD    Bitcoin USD (Crypto)
> ETH-USD    Ethereum USD
> GC=F       Gold Futures
> CL=F       Crude Oil Futures
> EURUSD=X   EUR/USD Exchange Rate
> USDJPY=X   USD/JPY Exchange Rate
> 2330.TW    TSMC (Taiwan)
> 2317.TW    Foxconn (Taiwan)
> 005930.KS  Samsung Electronics (Korea)
> 0700.HK    Tencent Holdings (Hong Kong)
> 601318.SS  Ping An (China A-Share)
> 600519.SS  Kweichow Moutai (China A-Share)
> ```

---

### 3.4 Remove Asset

1. In the "Prices" list (top right), click on the asset you want to remove
2. Click **"- Remove"** in the toolbar
3. Confirm in the dialog, select Yes

---

### 3.5 Update Prices

#### Update Current Watchlist

**Method:** Click **"Refresh WL"** in the toolbar

- Only updates assets in the currently selected Watchlist
- Does not affect prices in other Watchlists

#### Update All Prices

**Method:** Click **"Refresh All"** in the toolbar

- Updates all assets across all Watchlists
- Runs in **background threading** so the UI won't freeze
- Status bar displays "Updating... Please wait"
- After completion, the right panel updates in real-time:
  - Up: Red
  - Down: Green
  - Unchanged: Dark gray

Price field descriptions:

| Field  | Description                                                   |
| ------ | ------------------------------------------------------------- |
| Price  | Current market price (Yahoo Finance may be delayed 15-20 min) |
| Change | Today's price change amount                                   |
| % Chg  | Today's percentage change (%)                                 |
| Volume | Today's trading volume                                        |

---

### 3.6 Auto-Update

The program **automatically updates all prices every 10 minutes** when idle. No manual action required.

---

### 3.7 Candlestick Chart (Double-click Asset)

**How to use:** In the "Prices" list, **double-click** any asset row to open the candlestick chart window.

The candlestick chart window contains three subplots:

1. **Candlestick Chart** (top): Red for up, green for down, showing OHLC price movement
2. **Volume** (middle): Bar chart showing trading volume (normalized by max volume)
3. **KD Indicator** (bottom): K line (orange) and D line (blue) for buy/sell signals

Period switching:

- **Day**: Last 2 years of daily data
- **Week**: Last 10 years of weekly data
- **Month**: Last 30 years of monthly data

---

### 3.8 Right-click Menu (Fundamental Analysis, Technical Analysis, Related News)

In the "Prices" list, **right-click** any asset row to open the context menu:

| Option               | Description                                                                         |
| -------------------- | ----------------------------------------------------------------------------------- |
| Fundamental Analysis | Full financial analysis with 3 tabs: Fundamental / Technical / Categorized Analysis |
| Related News         | Displays the latest 10 news articles; click links to open in browser                |

---

### 3.9 Fundamental Analysis Window

Right-click an asset → **Fundamental Analysis** opens a three-tab window (1400×900):

#### Tab 1: Fundamental

Indicators include:

| Category           | Indicators                                                                                      |
| ------------------ | ----------------------------------------------------------------------------------------------- |
| Price Info         | Current Price, Change, % Change, Company Name                                                   |
| Valuation          | Market Cap, Trailing PE, Forward PE, PEG, Price/Book, EV/EBITDA                                 |
| Profitability      | EPS, ROE, ROA, ROIC, Operating Margin, Profit Margin                                            |
| Yield & Risk       | Dividend Yield, Beta, FCF Yield, Quick Ratio, Short %                                           |
| Analyst & Holdings | Analyst Avg/Median Target Price, Analyst Count, Recommendation Mean, Insider %, Institutional % |
| 52W Range          | 52W High, 52W Low, Range Position (current price's position between 52W high/low)               |
| Cash Flow          | Free Cash Flow (FCF), Operating Cash Flow, FCF Yield, FCF Dividend Coverage, ROIC               |
| Revenue & Growth   | Total Revenue, Total Liabilities, Total Cash, Earnings Growth, Revenue Growth                   |

#### Tab 2: Technical

Same as double-clicking an asset — displays K-line chart + Volume + KD indicator, with Day/Week/Month toggle.

#### Tab 3: Categorized Analysis

Card-based UI with 7 categories showing all key indicators at a glance:

| Category           | Included Indicators                                                                             |
| ------------------ | ----------------------------------------------------------------------------------------------- |
| Valuation          | Market Cap, Trailing PE, Forward PE, PEG, Price/Book, EV/EBITDA                                 |
| Profitability      | EPS, ROE, ROA, ROIC, Operating Margin, Profit Margin                                            |
| Yield & Risk       | Dividend Yield, Beta, FCF Yield, Quick Ratio, Short %                                           |
| Analyst & Holdings | Analyst Avg/Median Target Price, Analyst Count, Recommendation Mean, Insider %, Institutional % |
| 52W Range          | 52W High, 52W Low, Range Position                                                               |
| Cash Flow          | FCF, Operating Cash Flow, FCF Yield, FCF Dividend Coverage, ROIC                                |
| Revenue & Growth   | Total Revenue, Total Liabilities, Total Cash, Earnings Growth, Revenue Growth                   |

---

### 3.10 Related News

Right-click an asset → **Related News** displays:

- Latest 10 news articles
- Includes Publisher, Pub Date, and Title
- Click title or link to open article in browser

---

### 3.11 Price Alerts (⚙ Set Alert)

**How to set:**

1. Select an asset in the list
2. Click **"⚙ Set Alert"** in the toolbar
3. Enter a **High Price Alert** (notify when above this price) and/or **Low Price Alert** (notify when below this price)
4. Click **"Save"**

**Trigger behavior:**

- When price **rises above** the high alert, a Windows system notification (BalloonTip) appears: "🚨 High Alert: {ticker} rose to {price}"
- When price **drops below** the low alert, a notification appears: "📉 Low Alert: {ticker} dropped to {price}"
- Notification auto-dismisses after 12 seconds

**Managing alerts:**

- The menu shows all currently set alerts
- You can delete selected alerts or reset triggered states

---

### 3.12 Theme Switching (Theme)

Menu bar **Theme** → Options:

- 🌓 System: Follows Windows system settings
- ☀ Light: Light mode (white background, dark text)
- 🌙 Dark: Dark mode (dark background, light text)

---

### 3.13 Language Switching (Language)

Menu bar **Language** → Options:

- 繁體中文 (Traditional Chinese)
- 簡體中文 (Simplified Chinese)
- English
- 日本語 (Japanese)
- 한국어 (Korean)
- Español (Spanish)

Language and theme settings are automatically saved and restored on next launch.

---

### 3.14 Font & Font Size (Font / Font Family)

Menu bar **Font** → Adjust:

- **Size**: 10 ~ 20, drag slider to adjust
- **Font Family**: Choose from system-installed fonts (auto-detected)

Supported fonts include: Microsoft JhengHei, Arial, Tahoma, PMingLiU, DFKai-SB, SimHei, SimSun, and more.

---

### 3.15 Data Storage

The program automatically saves the following to `watchlist_data.json` (in the same directory as the program):

- All Watchlist contents
- Currently selected Watchlist
- Language setting
- Theme setting
- Font and font size
- All price alert settings

**Save timing:**

- **Saves immediately** on every Watchlist modification
- **Forces save again** when closing the program
- **Automatically loads** previous state on next launch

---

## 4. FAQ

### Q: Can I update a single Watchlist at a time?

A: Yes. Click **"Refresh WL"** to update only the currently selected Watchlist; click **"Refresh All"** to update all.

### Q: Is data persisted permanently?

A: Yes. The program automatically saves Watchlists, language, theme, font, and alert settings to `watchlist_data.json`, and restores automatically on next launch.

### Q: Can't find the ticker I'm looking for?

A:

1. Use **Method C (Direct Ticker Input)** and manually enter the official ticker
2. Common formats:
   - US stocks: `AAPL`, `GOOGL`
   - Crypto: `BTC-USD`, `ETH-USD`
   - Futures: `GC=F` (Gold), `CL=F` (Crude Oil)
   - Taiwan stocks: `2330.TW` on Yahoo Finance
   - Hong Kong stocks: `0700.HK`
   - China A-Shares: `601318.SS` (Shanghai), `000858.SZ` (Shenzhen)
   - Forex: `EURUSD=X`

### Q: Price updates are slow or failing?

A:

- yfinance requires internet connection; please verify your network
- Yahoo Finance occasionally rate-limits; if blocked due to heavy requests, wait and try again later
- The program has a built-in popular stock index (10,390+ stocks); the search function **works offline**

### Q: Candlestick chart won't display?

A:

- Make sure `matplotlib` is installed (`pip install matplotlib`)
- Some cryptocurrencies or forex pairs have limited data; candlestick chart may appear empty

### Q: Some text is hard to read in dark mode?

A: Dark mode has been optimized for contrast; if issues persist, try switching to System or Light theme, or adjust the font size.

### Q: How do I customize fonts?

A: Menu bar → **Font** → Select **Font Family** → Choose from system-installed fonts; or adjust **Size** to change font size (10-20).

---

## 5. Technical Architecture

| Component                 | Description                                                              |
| ------------------------- | ------------------------------------------------------------------------ |
| `yfinance`                | Fetches real-time stock prices and financial data from Yahoo Finance API |
| `tkinter` / `ttk`         | Python built-in GUI framework                                            |
| `matplotlib`              | Candlestick chart, volume, and KD indicator rendering                    |
| `threading`               | Background fetching to prevent UI freezing                               |
| `top250_tickers.json`     | Local index of 10,390+ popular stocks; search works offline              |
| `watchlist_data.json`     | Auto-saves all settings and data                                         |
| `subprocess` + PowerShell | Windows system notifications (BalloonTip)                                |

---

## 6. Quick Start (5 Minutes)

```
1. Launch the program
   > python watchlist_app.py

2. Click "US Large-Cap" on the left panel

3. The top-right table is pre-filled with major stocks; click "Refresh WL" to view real-time data

4. Create a new Watchlist:
   > Click "+ New Watchlist" → Enter "My Favorites" → OK

5. Add a stock (example: TSMC):
   > Select "My Favorites" on the left
   > Enter "2330" in the bottom-right search box
   > Double-click "2330.TW - TSMC" in the results
   > (Or directly input "2330.TW" and click "Direct Input")

6. Set a price alert:
   > Select TSMC → Click "⚙ Set Alert"
   > Set a High Price Alert (e.g., 1000) and/or Low Price Alert (e.g., 800)
   > Click "Save"

7. Double-click any asset → Opens candlestick chart (Day/Week/Month toggle)

8. Right-click any asset → Fundamental Analysis → Check the Categorized Analysis tab
```

Enjoy! 🎉