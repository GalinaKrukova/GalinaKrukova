# Internal Tools

## SM Connector

Internal tool

**Person of contact:** Alexey B (SMC team)

**Basic Description:** SM Connector is an internal Inca tool that allows for scraping data from various social media platforms (Twitter, Telegram, Reddit). The collected data can then be further processed (classified, geotagged, visualized, etc.).

**Link:** [https://1712n.github.io/inca-social-media-connector/](https://1712n.github.io/inca-social-media-connector/)

**How it works:**

One chooses the social media platform and the content to scrape, then fills out a form with the scraping details. After the scrape is completed, the data is saved in either MongoDB or AWS S3 depending on user’s choice.

Please note that for Twitter data requests, Inca possesses a limited quota. Please run an estimate of your query (’Number of Tweets’) before you run an actual query. If you are not sure about the amount of tweets to be pulled, please contact Alexey.

**Usage scenarios:**

- Scrape posts, followers, user info, mentions, tweets or estimate the amount of tweets from Twitter
- Scrape chat or channel messages, get chat members and join chats from Telegram
- Scrape comments and submission from Reddit

## Classification tool

Internal tool

**Person of contact:** Roman S

**Basic Description:** A classification tool is used for processing social media data and categorizing texts based on their relevance to one of five topics: downtime, hacker attacks, legal actions, security vulnerabilities, and withdrawal issues.

**How it works:**

- Prepare a .csv or .json file with all the posts to classify
- Message Roman S on the details, assign the issue and hand in the data (please coordinate with Investigations team lead (Christina T) on Roman’s workload)

**Usage scenarios:**

- Classified texts can be analyzed qualitatively and quantitatively.
- Classification data can be visualised on graphs

## Geotagging

Internal tool

**Person of contact:** Alexey B

**Basic Description:** Geotagging is a method of determining a user's location based on their social media posts. Inca Digital primarily analyzes Twitter posts for this purpose, but similar analysis can also be conducted using content from other social media platforms.

**How it works:**

- Prepare a list of Twitter usernames in a .csv file
- Assign an issue in GitHub for Alexey B (please coordinate with Investigations team lead (Christina T) on Alexey’s workload)

**Usage scenarios:**

- Locating users in restricted areas
- Gaining insights into audience location

## Labeling

**Person of contact:** Inga K

**Basic Description:** Labeling script based on ChatGPT. It can be utilized for different classification scenarios based on prompt for the model.

**Link:** [Google Drive](https://colab.research.google.com/drive/16pkr2OBT79kcU6ZBNHTlPyRsuCpSY_-D)

**How it works:**

- Get access to [API](https://platform.openai.com/) (contact Christina T)
- Follow the instructions on the script

**Usage scenarios:**

- Label users of a certain platform (e.g. Polymarket) or a service (e.g. VPN)
- Label risk-related posts (e.g. related to money laundering)

## APIs

[https://hub.inca.digital/hub](https://hub.inca.digital/hub)

### Cross-Market Surveillance

Internal tool

**Person of contact:** Marina C

**Basic Description:** The Cross-Market Surveillance API provides comprehensive market data analytics and surveillance across various cryptocurrency exchanges.

The API provides a comprehensive suite of tools for cryptocurrency market analysis and surveillance across various exchanges. It can be used to retrieve all metrics at once or just some of them (`metrics` request parameter), including only OHLCV and VWAP, making it possible to use for simple market data requests or comprehensive analysis. The **/dictionary** endpoint offers a broad overview of supported assets, exchanges, and trading pairs.

The **/metrics/market** endpoint delivers in-depth trading metrics for specific market venues, focusing on individual exchange-pair dynamics. Lastly, the **/metrics/pair** endpoint aggregates and analyzes trading data across all exchanges for a given pair, providing a holistic view of market behavior and trends. Together, these endpoints serve as valuable resources for traders, analysts, and regulatory bodies looking to understand and monitor the cryptocurrency market landscape.

**Website:** [https://hub.inca.digital/builders-organization-builders-organization-default/api/cross-market-surveillance1/](https://hub.inca.digital/builders-organization-builders-organization-default/api/cross-market-surveillance1/)

**How it works:** One needs to specify the market venue, pair, limit. If no parameters are specified, the endpoint returns a full list of assets.

**Usage scenarios:**

- Get market data for reports
- Visualize market data

### **BRAD API**

Internal tool

**Person of contact:** Kailee S

**Basic Description:** The Inca Digital BRAD API provides alerts for fintech entities across different topics based on social media data. The API supports an alert search by topic and entity.

The BRAD API supports the ability to search across any alert picked up from Inca Digital’s social media connectors by topics and entities. All documents are run through Inca Digital’s proprietary classification models and tagged with a score for their relevance to particular topics, with each alert triggered on anomaly. Supported topics can be filtered in the API using the topic query parameter.

Supported topics:

- hacker_attack
- security_issues
- withdrawal_issues
- downtime
- legal_actions
- bank_risk

**Website:** [https://hub.inca.digital/builders-organization-builders-organization-default/api/brad-api/](https://hub.inca.digital/builders-organization-builders-organization-default/api/brad-api/)

**How it works:** This endpoint retrieves alerts detected by EDS. Users can specify the event type and target entity to filter alerts. Optional parameters include start_date and end_date; if not provided, these default to a time range spanning the past 7 days.

**Usage scenarios:**

- Get information about alerts on a certain entity

### **RAD API**

Internal tool

**Person of contact:** Nick G

**Basic Description:** The Inca Digital RAD API provides social media data on relevant documents related to crypto ecosystem entities and topics. The API supports a rolling 2 weeks of historical social media data, in addition to text search and topic filtering on all recorded documents.

Currently supported topics include: downtime, legal_actions, security, hacker_attack, and withdrawals

**Website:** [https://hub.inca.digital/builders-organization-rd-team/api/rad-nlp/](https://hub.inca.digital/builders-organization-rd-team/api/rad-nlp/)

**How it works:** The RAD API supports the ability to search across any document picked up from Inca Digital’s social media connectors. The API supports handling of text search on document text bodies with the use of the search_text query parameter. Additionally, all documents are run through Inca Digital’s proprietary classification models and tagged with a score for their relevance to particular topics. Supported topics can be filtered in the API using the topic query parameter.

This API currently supports a rolling 2 weeks worth of social media data, and can be searched historically using the start_date and end_date parameters. For data beyond the scope of 2 weeks, please contact us at support@inca.digital for all custom requests.

Note that the use of the term document, refers to a tweet, reddit submission, or any other general form of post/text recorded by our social media connectors.

**Usage scenarios:**

- Get classified historical data from social media
- Classified texts could be analysed qualitatively and quantitatively.
- Classification data could be visualised on graphs

### **Cryptocurrency Market Data**

**Person of contact:** Marina C

Internal tool

**Basic Description:** **HISTORICAL** cryptocurrency financial data API for major exchanges. Provides OHLCV & VWAP metrics and Trade Level data. **Data available from January 1, 2020 to February 22, 2024. For later data, use the Cross Market Surveillance API, which offers OHLCV data and additional metrics.**

**Website:** [https://hub.inca.digital/builders-organization-builders-organization-default/api/cryptocurrency-market-data/](https://hub.inca.digital/builders-organization-builders-organization-default/api/cryptocurrency-market-data/)

**How it works:** Cryptocurrency financial data API offers access to historical data across multiple exchanges, including metadata, spot and futures candlesticks, and tick-level trades. OHLCV+VWAP metrics are derived from raw trades, available in 1m, 15m, 1h, and 1d granularity. Historical data is available from the beginning of 2020 until February 22, 2024. For data beyond this date, use the Cross Market Surveillance API, which provides OHLCV data and other metrics. Contact market.data@inca.digital for API feedback.

**Usage scenarios:**

- Display real-time prices in apps or dashboards.
- Analyze past prices for trends and strategies.
- Investigate price differences across exchanges.

### **Stablecoin Depeg Detection**

**Person of contact:** Marina C

Internal tool

**Basic Description:** The Stablecoin Depeg Detection API provides historical monitoring and analysis of potential depegging events for various USD-pegged stablecoins.

**Website:** [https://hub.inca.digital/builders-organization-builders-organization-default/api/stablecoin-depeg-detection/](https://hub.inca.digital/builders-organization-builders-organization-default/api/stablecoin-depeg-detection/)

**How it works:** The API calculates the deviation from the $1 peg based on the specified time range, stablecoin pair, and user-defined threshold. The data is available since February 2024 and has an approximate delay of 20 minutes.

**Usage scenarios:**

- Notify users of stablecoin price deviations.
- Track stablecoins and prevent losses from depegging.
- Trigger smart contracts when stablecoins depeg.

## Dashboards

### RAD (Real-time Anomaly Detection)

**Person of contact:** Nick G

**Basic Description:** This dashboard uses social media data to detect and alert users to unusual activity in the following areas: downtime, hacker attacks, legal actions, withdrawals, and security issues. The dashboard monitors social media activity for a specified number of entities, including different crypto exchanges, cryptocurrencies, and banks. Social media data is collected from Twitter, Mastodon, Reddit, Telegram, and other social media platforms are currently being added.

**Splunk dashboards:**

- [RAD Demo Dashboard](https://splunk.mithraslabs.com/en-US/app/search/rad_dashboard?form.global_time.earliest=2024-01-05T00%3A00%3A00.000Z&form.global_time.latest=2024-03-06T00%3A00%3A00.000Z&form.risk_label=Overall&form.entity=JP+Morgan) showcases some of RAD’s capabilities. This particular demo includes approximately 10 banks and categorises social media posts as risk-related or not risk-related. It further breaks down the posts based on the type of risk identified, such as hack or downtime, etc. The dashboard also includes sample posts.
- [Scam & Fraud/RAD Sample Dashboard](https://splunk.mithraslabs.com/en-US/app/search/scam__fraud_sample_dashboard?form.entity=%22JP+Morgan%22) demonstrates some potential capabilities of RAD. Notably, it includes “risk scoring,” although this isn’t based on a genuine risk assessment method but rather on sentiment analysis. While this isn’t a direct product for us, sentiment analysis is a capability we can utilise. The second half of the dashboard focuses on scam and fraud analysis, as well as mapping.
- [SVB Data](https://splunk.mithraslabs.com/en-US/app/search/svb_data?form.time_granularity=1h) displays the Silicon Valley Bank data we possess, along with how our RAD product categorises posts. It serves as a testament to our ability to detect the SVB attack before it occurred, exemplifying the principles of BRAD.

### XMS (X-Market Surveillance)

**Person of contact:** Marina C

**Basic Description:** This dashboard offers a comprehensive overview of market data, providing insights into market manipulations and other illicit activities involving specific pairs and exchanges. It detects manipulative practices such as Wash Trading, Spoofing, Layering, and Pump and Dump by analyzing key indicators, including abnormal volume distributions, unusual trade size clustering, trade timing anomalies, and first-digit distribution deviations. By leveraging metrics like tail exponent shifts, skewness and kurtosis, Student’s test for trade-size clustering, Kolmogorov-Smirnov tests for trade timing and first-digit distribution, as well as liquidity metrics such as VWAP, average spread distance, and order flow imbalance, the dashboard uncovers irregular trading behaviors and enhances transparency across markets.

**Splunk Dashboards:**

- [XMS Dashboard Demo](https://splunk.mithraslabs.com/en-US/app/search/xms_dashboard_demo?form.token_time_selector.earliest=1719360000&form.token_time_selector.latest=1719446400&form.assettype=spot&form.symbol=btc&form.base=usdt&form.marketvenue=ASCENDEX%22%2C%22BINANCE%22%2C%22BINANCEUS%22%2C%22BITFINEX%22%2C%22BITMEX%22%2C%22BITSTAMP%22%2C%22BYBIT%22%2C%22COINBASE%22%2C%22CRYPTOCOM%22%2C%22DELTA%22%2C%22DERIBIT%22%2C%22GATEIO%22%2C%22GEMINI%22%2C%22HTX%22%2C%22KRAKEN%22%2C%22KUCOIN%22%2C%22OKX%22%2C%22PHEMEX%22%2C%22POLONIEX%22%2C%22UPBIT&form.section=benford&form.trellisoption_benford=0&form.bin_size=5&form.trellisoption_volume=0&form.trellisoption_time=0) – This dashboard, created by XMS Team, serves as an overview of all available metrics.
- [XMS Metrics Example](https://splunk.mithraslabs.com/en-US/app/search/xms_metrics?form.filename=sample_dataset&form.dt_format=%25m%2F%25d%2F%25Y%20%25H%3A%25M) – This is an example dashboard built to show one use case for XMS data.

### Stablecoin Dashboard

**Person of contact:** Kailee S

**Basic Description:** This dashboard features some stablecoin metrics including market cap, XMS, mint/burn data, etc. It also has threat intelligence examples including geotagging, impersonations, scam analysis, fake tokens. The threat intelligence examples are for Ripple, but it is a good example of what we could do for other clients and projects.

**Splunk Dashboards:**

- [Stablecoin Metrics and Ripple Threat Intelligence](https://splunk.mithraslabs.com/en-US/app/search/stablecoin_metrics_wip__ripple_marketing?form.start_date=2024-01-01&form.end_date=2025-01-23&form.mint_burn_stablecoin=*&form.stablecoin=*&form.marketplace=Kraken&form.pair=usdt-usd&form.granularity=1d)
