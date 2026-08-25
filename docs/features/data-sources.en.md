# Data Sources

No data? No problem. DeepResValue's data acquisition capability operates on two levels: **built-in panel datasets** and **skill-driven data collection** from external sources. Describe your needs in Chinese and the AI automatically matches the appropriate data source.

## Built-in Panel Data

The data engine directly reads authoritative Parquet files, covering six datasets:

| Dataset | Coverage |
|---------|----------|
| 📊 **City Macro Panel** | 2000–2023, 325 indicators including GDP, population, employment, industry, finance, trade |
| 🏙️ **Provincial Macro Panel** | 2000–2023, 2,468 indicators covering population, economy, education, employment |
| 🏘️ **County Panel** | 2000–2023, 61 indicators covering population, economy, education, health |
| 💼 **Listed Company Financials** | 2000–2023, 30 core financial indicators |
| 🏢 **Listed Company Governance** | 2000–2023, 84 indicators covering financials, governance, market data |
| 📍 **Industry & Geography** | 2000–2023, stock codes, industry classification, province location |

## Skill-Driven Data Collection

AI automatically loads the appropriate data collection skill to fetch structured data from external sources:

| Domain | Available Data |
|--------|---------------|
| 📈 **Financial Markets** | A-share/index/industry real-time and historical quotes; A-share/HK/US stocks, funds, bonds, macro EDB |
| 🏭 **Chinese Economic Data** | Province/city/county regional panels (1990–2024), listed company financials (5,822 companies / 857 indicators), firm geolocation, spatial boundaries |
| 🗺️ **Chinese Spatial Data** | Province/city/county administrative boundary GeoJSON, GB/T 2260 codes |
| 🏥 **US Health Data** | NHANES, BRFSS, NHIS, NVSS, WONDER (CDC public data) |
| ⚕️ **Medical Databases** | ClinicalTrials.gov, WHO Global Health, PubChem, MeSH/RxNorm, NCBI gene data |
| 🧬 **Biological Data** | EMBL-EBI databases, bioRxiv preprints |
| 📚 **Literature Search** | NCPSSD Chinese journals, CNKI enhanced abstracts, arXiv preprints, PubMed biomedical, Crossref metadata |
| 🌐 **Web Content** | Extract main text from specified URLs |

## MCP External Connectors

The platform has integrated **dozens of MCP connectors**, letting you call third-party professional data sources directly in conversation — without leaving the platform. The AI automatically determines when to invoke connectors; you can also trigger them explicitly.

| Connector | Type | Description |
|-----------|------|-------------|
| **PatSnap (智慧芽)** ★ | Patent & IP | 34 official MCP services: patent search/analysis/valuation/landscape, clinical trials, drug assets, target-disease mapping, regulatory guidance, TRIZ engine, etc. |
| **PKULaw (北大法宝)** | Legal Search | Chinese laws, regulations, judicial cases, academic journals |
| **Wind (万得)** | Financial Data | Listed company financials, macroeconomic data, industry data |
| **iFinD (同花顺)** | Financial Markets | A-share, public funds, macro data, bonds, financial news |
| **Qichacha (企查查)** | Business Intelligence | Business registration, risk, IP, operations, historical data |
| **Baidu AI Academic** | Academic Search | AI-powered academic literature search |
| **Baidu Wenku / OCR** | Document Processing | Literature image recognition, document parsing |
| **Open Academic Suite** | Academic Metadata | arXiv, PubMed, Crossref, Semantic Scholar (no auth required) |
| **Tencent Maps** | Geolocation | Geocoding, POI search, route planning |
| **Tencent Survey / Meeting** | Collaboration | Survey research, meeting minutes |
| **TickDB** | Quantitative Data | Forex, precious metals, indices, US/HK/A-share, crypto quantitative data |

> Connectors are continuously expanding. Some connectors (e.g., PKULaw, Wind) require your own API Token (BYOK) — the platform charges no additional service fee.

## Usage

1. **Describe your data needs** — In the chat, state in Chinese what data type, time range, and variables you need.
2. **AI auto-matches the source** — The AI determines whether the data is available in built-in panels or needs external collection, then automatically loads the appropriate skill.
3. **Use directly for analysis** — Retrieved data can be immediately used for statistical analysis in the current conversation.

## Example Prompts

> "Find 2015–2023 prefecture-level city GDP and fiscal revenue data."

> "Get a listed company's financial indicators (revenue, net profit, debt-to-asset ratio) for the past 5 years."

> "Search for NHANES survey BMI data for adults from 2017–2020."

> "Find recent 3-year PubMed literature on digital economy and carbon emissions."

> Describe your needs and the AI handles the rest — **free, no intermediary, no complex queries**.
