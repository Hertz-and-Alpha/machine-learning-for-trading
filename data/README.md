# 책에서 사용되는 데이터 소드들 저장

우리는 시장, 기초 자료 및 대체 자료에서 무료로 이용할 수 있는 과거 데이터를 사용할 것입니다. 제2장 "시장 및 기초 데이터"와 제3장 "금융을 위한 대안 데이터"는 이러한 데이터 소스에 대한 특성 및 액세스에 대해 다루며, 본 책 전반에 걸쳐 사용할 주요 공급자를 소개합니다.

샘플 데이터 소스는 다음과 같습니다.
- Quandl daily prices and other data points for over 3,000 US stocks
- Algoseek minute bar trade and quote price data for NASDAQ 100 stocks
- Stooq daily price data on Japanese equities and US ETFs and stocks
- Yahoo finance daily price data and fundamentals for US stocks  
- NASDAQ ITCH order book data
- Electronic Data Gathering, Analysis, and Retrieval (EDGAR) SEC filings
- Earnings call transcripts from Seeking Alpha
- Various macro fundamental data from the Federal Reserve and others
- Financial news data from Reuters, etc.
- Twitter sentiment data
- Yelp business reviews sentiment data

## 데이터 소싱 방법

데이터 소싱 프로세스를 안내하는 여러 노트북이 있습니다.
- 노트북 [create_datasets](create_datasets.ipynb)에는 **Quandl Wiki 주가** 다운로드에 대한 정보와 S&P500 벤치마크 및 미국 주식 메타데이터와 같은 기타 몇 가지 소스가 포함되어 있습니다.
- 노트북 [create_stooq_data](create_stooq_data.ipynb)에서는 일본 주식 및 미국 주식과 ETF의 과거 가격을 STOOQ에서 다운로드하는 방법을 알려줍니다.
> STOOQ는 2020년 12월 10일부터 자동 다운로드를 비활성화하며 zip 파일을 다운로드하고 압축을 푸는 코드가 더 이상 작동하지 않도록 돼서 사이트에 직접 들어가서 다운로드를 받아야 됩니다. 다운로드를 할때 CAPTCHA를 요구합니다. 수동 다운로드를 위해 웹 사이트를 탐색하십시오.
- 노트북 [create_yelp_review_data](create_yelp_review_data.ipynb)은 텍스트 데이터와 Yelp 사용자 리뷰의 정서 분석을 위한 추가적인 수치 기능을 추가한 것입니다.
- 노트북 [globe_word_vectors](globe_word_vectors.ipynb)에서 사전에 만들어진 워드 벡터를 다운로드합니다.
- 노트북 [twitter_sentiment](twitter_sentiment.ipynb)에서 감성 분석을 위한 트위터 데이터를 다운로드 및 추출합니다.

또한 특정 응용 프로그램의 데이터 소스를 얻기 위한 지침이 관련 디렉토리 및 노트북에 제공됩니다.
