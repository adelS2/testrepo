<p style="text-align:center">
    <a href="https://skills.network/?utm_medium=Exinfluencer&utm_source=Exinfluencer&utm_content=000026UJ&utm_term=10006555&utm_id=NA-SkillsNetwork-Channel-SkillsNetworkCoursesIBMDeveloperSkillsNetworkPY0220ENSkillsNetwork900-2022-01-01" target="_blank">
    <img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/assets/logos/SN_web_lightmode.png" width="200" alt="Skills Network Logo">
    </a>
</p>


<h1>Extracting and Visualizing Stock Data</h1>
<h2>Description</h2>


Extracting essential data from a dataset and displaying it is a necessary part of data science; therefore individuals can make correct decisions based on the data. In this assignment, you will extract some stock data, you will then display this data in a graph.


<h2>Table of Contents</h2>
<div class="alert alert-block alert-info" style="margin-top: 20px">
    <ul>
        <li>Define a Function that Makes a Graph</li>
        <li>Question 1: Use yfinance to Extract Stock Data</li>
        <li>Question 2: Use Webscraping to Extract Tesla Revenue Data</li>
        <li>Question 3: Use yfinance to Extract Stock Data</li>
        <li>Question 4: Use Webscraping to Extract GME Revenue Data</li>
        <li>Question 5: Plot Tesla Stock Graph</li>
        <li>Question 6: Plot GameStop Stock Graph</li>
    </ul>
<p>
    Estimated Time Needed: <strong>30 min</strong></p>
</div>

<hr>


***Note***:- If you are working Locally using anaconda, please uncomment the following code and execute it.
Use the version as per your python version.



```python
!pip install yfinance
!pip install bs4
!pip install nbformat
```

    Collecting yfinance
      Downloading yfinance-0.2.52-py2.py3-none-any.whl.metadata (5.8 kB)
    Collecting pandas>=1.3.0 (from yfinance)
      Downloading pandas-2.2.3-cp312-cp312-manylinux_2_17_x86_64.manylinux2014_x86_64.whl.metadata (89 kB)
    Collecting numpy>=1.16.5 (from yfinance)
      Downloading numpy-2.2.2-cp312-cp312-manylinux_2_17_x86_64.manylinux2014_x86_64.whl.metadata (62 kB)
    Requirement already satisfied: requests>=2.31 in /opt/conda/lib/python3.12/site-packages (from yfinance) (2.32.3)
    Collecting multitasking>=0.0.7 (from yfinance)
      Downloading multitasking-0.0.11-py3-none-any.whl.metadata (5.5 kB)
    Collecting lxml>=4.9.1 (from yfinance)
      Downloading lxml-5.3.0-cp312-cp312-manylinux_2_28_x86_64.whl.metadata (3.8 kB)
    Requirement already satisfied: platformdirs>=2.0.0 in /opt/conda/lib/python3.12/site-packages (from yfinance) (4.3.6)
    Requirement already satisfied: pytz>=2022.5 in /opt/conda/lib/python3.12/site-packages (from yfinance) (2024.2)
    Requirement already satisfied: frozendict>=2.3.4 in /opt/conda/lib/python3.12/site-packages (from yfinance) (2.4.6)
    Collecting peewee>=3.16.2 (from yfinance)
      Downloading peewee-3.17.8.tar.gz (948 kB)
    [2K     [90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━[0m [32m948.2/948.2 kB[0m [31m26.7 MB/s[0m eta [36m0:00:00[0m
      Installing build dependencies ... [?done
    [?25h  Getting requirements to build wheel ... [?25ldone
    [?25h  Preparing metadata (pyproject.toml) ... [?25ldone
    [?25hRequirement already satisfied: beautifulsoup4>=4.11.1 in /opt/conda/lib/python3.12/site-packages (from yfinance) (4.12.3)
    Collecting html5lib>=1.1 (from yfinance)
      Downloading html5lib-1.1-py2.py3-none-any.whl.metadata (16 kB)
    Requirement already satisfied: soupsieve>1.2 in /opt/conda/lib/python3.12/site-packages (from beautifulsoup4>=4.11.1->yfinance) (2.5)
    Requirement already satisfied: six>=1.9 in /opt/conda/lib/python3.12/site-packages (from html5lib>=1.1->yfinance) (1.17.0)
    Requirement already satisfied: webencodings in /opt/conda/lib/python3.12/site-packages (from html5lib>=1.1->yfinance) (0.5.1)
    Requirement already satisfied: python-dateutil>=2.8.2 in /opt/conda/lib/python3.12/site-packages (from pandas>=1.3.0->yfinance) (2.9.0.post0)
    Collecting tzdata>=2022.7 (from pandas>=1.3.0->yfinance)
      Downloading tzdata-2024.2-py2.py3-none-any.whl.metadata (1.4 kB)
    Requirement already satisfied: charset_normalizer<4,>=2 in /opt/conda/lib/python3.12/site-packages (from requests>=2.31->yfinance) (3.4.1)
    Requirement already satisfied: idna<4,>=2.5 in /opt/conda/lib/python3.12/site-packages (from requests>=2.31->yfinance) (3.10)
    Requirement already satisfied: urllib3<3,>=1.21.1 in /opt/conda/lib/python3.12/site-packages (from requests>=2.31->yfinance) (2.3.0)
    Requirement already satisfied: certifi>=2017.4.17 in /opt/conda/lib/python3.12/site-packages (from requests>=2.31->yfinance) (2024.12.14)
    Downloading yfinance-0.2.52-py2.py3-none-any.whl (108 kB)
    Downloading html5lib-1.1-py2.py3-none-any.whl (112 kB)
    Downloading lxml-5.3.0-cp312-cp312-manylinux_2_28_x86_64.whl (4.9 MB)
    [2K   [90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━[0m [32m4.9/4.9 MB[0m [31m87.4 MB/s[0m eta [36m0:00:00[0m
    [?25hDownloading multitasking-0.0.11-py3-none-any.whl (8.5 kB)
    Downloading numpy-2.2.2-cp312-cp312-manylinux_2_17_x86_64.manylinux2014_x86_64.whl (16.1 MB)
    [2K   [90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━[0m [32m16.1/16.1 MB[0m [31m116.4 MB/s[0m eta [36m0:00:00[0m
    [?25hDownloading pandas-2.2.3-cp312-cp312-manylinux_2_17_x86_64.manylinux2014_x86_64.whl (12.7 MB)
    [2K   [90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━[0m [32m12.7/12.7 MB[0m [31m126.4 MB/s[0m eta [36m0:00:00[0m
    [?25hDownloading tzdata-2024.2-py2.py3-none-any.whl (346 kB)
    Building wheels for collected packages: peewee
      Building wheel for peewee (pyproject.toml) ... [?done
    [?25h  Created wheel for peewee: filename=peewee-3.17.8-cp312-cp312-linux_x86_64.whl size=303769 sha256=33c5690500db8132db70a3d8f295438d0698c22398cad4bb16c8845d158d774c
      Stored in directory: /home/jupyterlab/.cache/pip/wheels/8f/65/34/456800445efeafb05164fe95285c70e81ba1d96bae30f43917
    Successfully built peewee
    Installing collected packages: peewee, multitasking, tzdata, numpy, lxml, html5lib, pandas, yfinance
    Successfully installed html5lib-1.1 lxml-5.3.0 multitasking-0.0.11 numpy-2.2.2 pandas-2.2.3 peewee-3.17.8 tzdata-2024.2 yfinance-0.2.52
    Collecting bs4
      Downloading bs4-0.0.2-py2.py3-none-any.whl.metadata (411 bytes)
    Requirement already satisfied: beautifulsoup4 in /opt/conda/lib/python3.12/site-packages (from bs4) (4.12.3)
    Requirement already satisfied: soupsieve>1.2 in /opt/conda/lib/python3.12/site-packages (from beautifulsoup4->bs4) (2.5)
    Downloading bs4-0.0.2-py2.py3-none-any.whl (1.2 kB)
    Installing collected packages: bs4
    Successfully installed bs4-0.0.2
    Requirement already satisfied: nbformat in /opt/conda/lib/python3.12/site-packages (5.10.4)
    Requirement already satisfied: fastjsonschema>=2.15 in /opt/conda/lib/python3.12/site-packages (from nbformat) (2.21.1)
    Requirement already satisfied: jsonschema>=2.6 in /opt/conda/lib/python3.12/site-packages (from nbformat) (4.23.0)
    Requirement already satisfied: jupyter-core!=5.0.*,>=4.12 in /opt/conda/lib/python3.12/site-packages (from nbformat) (5.7.2)
    Requirement already satisfied: traitlets>=5.1 in /opt/conda/lib/python3.12/site-packages (from nbformat) (5.14.3)
    Requirement already satisfied: attrs>=22.2.0 in /opt/conda/lib/python3.12/site-packages (from jsonschema>=2.6->nbformat) (24.3.0)
    Requirement already satisfied: jsonschema-specifications>=2023.03.6 in /opt/conda/lib/python3.12/site-packages (from jsonschema>=2.6->nbformat) (2024.10.1)
    Requirement already satisfied: referencing>=0.28.4 in /opt/conda/lib/python3.12/site-packages (from jsonschema>=2.6->nbformat) (0.35.1)
    Requirement already satisfied: rpds-py>=0.7.1 in /opt/conda/lib/python3.12/site-packages (from jsonschema>=2.6->nbformat) (0.22.3)
    Requirement already satisfied: platformdirs>=2.5 in /opt/conda/lib/python3.12/site-packages (from jupyter-core!=5.0.*,>=4.12->nbformat) (4.3.6)



```python
import yfinance as yf
import pandas as pd1
import requests
from bs4 import BeautifulSoup
import plotly.graph_objects as go
from plotly.subplots import make_subplots
```

In Python, you can ignore warnings using the warnings module. You can use the filterwarnings function to filter or ignore specific warning messages or categories.



```python
import warnings
# Ignore all warnings
warnings.filterwarnings("ignore", category=FutureWarning)
```

## Define Graphing Function


In this section, we define the function `make_graph`. **You don't have to know how the function works, you should only care about the inputs. It takes a dataframe with stock data (dataframe must contain Date and Close columns), a dataframe with revenue data (dataframe must contain Date and Revenue columns), and the name of the stock.**



```python
def make_graph(stock_data, revenue_data, stock):
    fig = make_subplots(rows=2, cols=1, shared_xaxes=True, subplot_titles=("Historical Share Price", "Historical Revenue"), vertical_spacing = .3)
    stock_data_specific = stock_data[stock_data.Date <= '2021-06-14']
    revenue_data_specific = revenue_data[revenue_data.Date <= '2021-04-30']
    fig.add_trace(go.Scatter(x=pd.to_datetime(stock_data_specific.Date, infer_datetime_format=True), y=stock_data_specific.Close.astype("float"), name="Share Price"), row=1, col=1)
    fig.add_trace(go.Scatter(x=pd.to_datetime(revenue_data_specific.Date, infer_datetime_format=True), y=revenue_data_specific.Revenue.astype("float"), name="Revenue"), row=2, col=1)
    fig.update_xaxes(title_text="Date", row=1, col=1)
    fig.update_xaxes(title_text="Date", row=2, col=1)
    fig.update_yaxes(title_text="Price ($US)", row=1, col=1)
    fig.update_yaxes(title_text="Revenue ($US Millions)", row=2, col=1)
    fig.update_layout(showlegend=False,
    height=900,
    title=stock,
    xaxis_rangeslider_visible=True)
    fig.show()
```

Use the make_graph function that we’ve already defined. You’ll need to invoke it in questions 5 and 6 to display the graphs and create the dashboard. 
> **Note: You don’t need to redefine the function for plotting graphs anywhere else in this notebook; just use the existing function.**


## Question 1: Use yfinance to Extract Stock Data


Using the `Ticker` function enter the ticker symbol of the stock we want to extract data on to create a ticker object. The stock is Tesla and its ticker symbol is `TSLA`.



```python


import yfinance as yf

tesla = yf.Ticker("TSLA")

historical_data = tesla.history(period="1mo")  # Last 1 month of data
print(historical_data)

info = tesla.info
print(info)

financials = tesla.financials
print(financials)
```

                                     Open        High         Low       Close  \
    Date                                                                        
    2024-12-18 00:00:00-05:00  466.500000  488.540009  427.010010  440.130005   
    2024-12-19 00:00:00-05:00  451.880005  456.359985  420.019989  436.170013   
    2024-12-20 00:00:00-05:00  425.510010  447.079987  417.640015  421.059998   
    2024-12-23 00:00:00-05:00  431.000000  434.510010  415.410004  430.600006   
    2024-12-24 00:00:00-05:00  435.899994  462.779999  435.140015  462.279999   
    2024-12-26 00:00:00-05:00  465.160004  465.329987  451.019989  454.130005   
    2024-12-27 00:00:00-05:00  449.519989  450.000000  426.500000  431.660004   
    2024-12-30 00:00:00-05:00  419.399994  427.000000  415.750000  417.410004   
    2024-12-31 00:00:00-05:00  423.790009  427.929993  402.540009  403.839996   
    2025-01-02 00:00:00-05:00  390.100006  392.730011  373.040009  379.279999   
    2025-01-03 00:00:00-05:00  381.480011  411.880005  379.450012  410.440002   
    2025-01-06 00:00:00-05:00  423.200012  426.429993  401.700012  411.049988   
    2025-01-07 00:00:00-05:00  405.829987  414.329987  390.000000  394.359985   
    2025-01-08 00:00:00-05:00  392.950012  402.500000  387.399994  394.940002   
    2025-01-10 00:00:00-05:00  391.399994  399.279999  377.290009  394.739990   
    2025-01-13 00:00:00-05:00  383.209991  403.790009  380.070007  403.309998   
    2025-01-14 00:00:00-05:00  414.339996  422.640015  394.540009  396.359985   
    2025-01-15 00:00:00-05:00  409.899994  429.799988  405.660004  428.220001   
    2025-01-16 00:00:00-05:00  423.489990  424.000000  409.130005  413.820007   
    2025-01-17 00:00:00-05:00  421.500000  439.739990  419.750000  426.500000   
    
                                  Volume  Dividends  Stock Splits  
    Date                                                           
    2024-12-18 00:00:00-05:00  149340800        0.0           0.0  
    2024-12-19 00:00:00-05:00  118566100        0.0           0.0  
    2024-12-20 00:00:00-05:00  132216200        0.0           0.0  
    2024-12-23 00:00:00-05:00   72698100        0.0           0.0  
    2024-12-24 00:00:00-05:00   59551800        0.0           0.0  
    2024-12-26 00:00:00-05:00   76366400        0.0           0.0  
    2024-12-27 00:00:00-05:00   82666800        0.0           0.0  
    2024-12-30 00:00:00-05:00   64941000        0.0           0.0  
    2024-12-31 00:00:00-05:00   76825100        0.0           0.0  
    2025-01-02 00:00:00-05:00  109710700        0.0           0.0  
    2025-01-03 00:00:00-05:00   95423300        0.0           0.0  
    2025-01-06 00:00:00-05:00   85516500        0.0           0.0  
    2025-01-07 00:00:00-05:00   75699500        0.0           0.0  
    2025-01-08 00:00:00-05:00   73038800        0.0           0.0  
    2025-01-10 00:00:00-05:00   62287300        0.0           0.0  
    2025-01-13 00:00:00-05:00   67580500        0.0           0.0  
    2025-01-14 00:00:00-05:00   84565000        0.0           0.0  
    2025-01-15 00:00:00-05:00   81375500        0.0           0.0  
    2025-01-16 00:00:00-05:00   68335200        0.0           0.0  
    2025-01-17 00:00:00-05:00   94504200        0.0           0.0  
    {'address1': '1 Tesla Road', 'city': 'Austin', 'state': 'TX', 'zip': '78725', 'country': 'United States', 'phone': '512 516 8177', 'website': 'https://www.tesla.com', 'industry': 'Auto Manufacturers', 'industryKey': 'auto-manufacturers', 'industryDisp': 'Auto Manufacturers', 'sector': 'Consumer Cyclical', 'sectorKey': 'consumer-cyclical', 'sectorDisp': 'Consumer Cyclical', 'longBusinessSummary': 'Tesla, Inc. designs, develops, manufactures, leases, and sells electric vehicles, and energy generation and storage systems in the United States, China, and internationally. The company operates in two segments, Automotive, and Energy Generation and Storage. The Automotive segment offers electric vehicles, as well as sells automotive regulatory credits; and non-warranty after-sales vehicle, used vehicles, body shop and parts, supercharging, retail merchandise, and vehicle insurance services. This segment also provides sedans and sport utility vehicles through direct and used vehicle sales, a network of Tesla Superchargers, and in-app upgrades; purchase financing and leasing services; services for electric vehicles through its company-owned service locations and Tesla mobile service technicians; and vehicle limited warranties and extended service plans. The Energy Generation and Storage segment engages in the design, manufacture, installation, sale, and leasing of solar energy generation and energy storage products, and related services to residential, commercial, and industrial customers and utilities through its website, stores, and galleries, as well as through a network of channel partners; and provision of service and repairs to its energy product customers, including under warranty, as well as various financing options to its solar customers. The company was formerly known as Tesla Motors, Inc. and changed its name to Tesla, Inc. in February 2017. Tesla, Inc. was incorporated in 2003 and is headquartered in Austin, Texas.', 'fullTimeEmployees': 140473, 'companyOfficers': [{'maxAge': 1, 'name': 'Mr. Elon R. Musk', 'age': 52, 'title': 'Co-Founder, Technoking of Tesla, CEO & Director', 'yearBorn': 1972, 'fiscalYear': 2023, 'exercisedValue': 0, 'unexercisedValue': 0}, {'maxAge': 1, 'name': 'Mr. Vaibhav  Taneja', 'age': 46, 'title': 'Chief Financial Officer', 'yearBorn': 1978, 'fiscalYear': 2023, 'totalPay': 278000, 'exercisedValue': 8517957, 'unexercisedValue': 202075632}, {'maxAge': 1, 'name': 'Mr. Xiaotong  Zhu', 'age': 44, 'title': 'Senior Vice President of Automotive', 'yearBorn': 1980, 'fiscalYear': 2023, 'totalPay': 926877, 'exercisedValue': 0, 'unexercisedValue': 344144320}, {'maxAge': 1, 'name': 'Travis  Axelrod', 'title': 'Head of Investor Relations', 'fiscalYear': 2023, 'exercisedValue': 0, 'unexercisedValue': 0}, {'maxAge': 1, 'name': 'Brian  Scelfo', 'title': 'Senior Director of Corporate Development', 'fiscalYear': 2023, 'exercisedValue': 0, 'unexercisedValue': 0}, {'maxAge': 1, 'name': 'Mr. Franz  von Holzhausen', 'title': 'Chief Designer', 'fiscalYear': 2023, 'exercisedValue': 0, 'unexercisedValue': 0}, {'maxAge': 1, 'name': 'Mr. John  Walker', 'age': 61, 'title': 'Vice President of Sales - North America', 'yearBorn': 1963, 'fiscalYear': 2023, 'totalPay': 121550, 'exercisedValue': 0, 'unexercisedValue': 0}, {'maxAge': 1, 'name': 'Mr. Peter  Bannon', 'title': 'Chip Architect', 'fiscalYear': 2023, 'exercisedValue': 0, 'unexercisedValue': 0}, {'maxAge': 1, 'name': 'Mr. Turner  Caldwell', 'title': 'Engineering Manager', 'fiscalYear': 2023, 'exercisedValue': 0, 'unexercisedValue': 0}, {'maxAge': 1, 'name': 'Mr. Rodney D. Westmoreland Jr.', 'title': 'Director of Construction Management', 'fiscalYear': 2023, 'exercisedValue': 0, 'unexercisedValue': 0}], 'auditRisk': 5, 'boardRisk': 9, 'compensationRisk': 10, 'shareHolderRightsRisk': 9, 'overallRisk': 10, 'governanceEpochDate': 1735689600, 'compensationAsOfEpochDate': 1703980800, 'maxAge': 86400, 'priceHint': 2, 'previousClose': 413.82, 'open': 421.72, 'dayLow': 419.7701, 'dayHigh': 439.74, 'regularMarketPreviousClose': 413.82, 'regularMarketOpen': 421.72, 'regularMarketDayLow': 419.7701, 'regularMarketDayHigh': 439.74, 'beta': 2.295, 'trailingPE': 116.21253, 'forwardPE': 130.76765, 'volume': 94991429, 'regularMarketVolume': 94991429, 'averageVolume': 94093459, 'averageVolume10days': 78832580, 'averageDailyVolume10Day': 78832580, 'marketCap': 1369090555904, 'fiftyTwoWeekLow': 138.8, 'fiftyTwoWeekHigh': 488.54, 'priceToSalesTrailing12Months': 14.092543, 'fiftyDayAverage': 381.2156, 'twoHundredDayAverage': 251.5414, 'currency': 'USD', 'enterpriseValue': 1349004427264, 'profitMargins': 0.13075, 'floatShares': 2793105010, 'sharesOutstanding': 3210060032, 'sharesShort': 67379077, 'sharesShortPriorMonth': 77192871, 'sharesShortPreviousMonthDate': 1732838400, 'dateShortInterest': 1735603200, 'sharesPercentSharesOut': 0.021, 'heldPercentInsiders': 0.12903, 'heldPercentInstitutions': 0.48031, 'shortRatio': 0.74, 'shortPercentOfFloat': 0.0241, 'impliedSharesOutstanding': 3210060032, 'bookValue': 21.806, 'priceToBook': 19.558838, 'lastFiscalYearEnd': 1703980800, 'nextFiscalYearEnd': 1735603200, 'mostRecentQuarter': 1727654400, 'earningsQuarterlyGrowth': 0.169, 'netIncomeToCommon': 12743000064, 'trailingEps': 3.67, 'forwardEps': 3.24, 'lastSplitFactor': '3:1', 'lastSplitDate': 1661385600, 'enterpriseToRevenue': 13.886, 'enterpriseToEbitda': 101.858, '52WeekChange': 1.0426245, 'SandP52WeekChange': 0.23631513, 'exchange': 'NMS', 'quoteType': 'EQUITY', 'symbol': 'TSLA', 'underlyingSymbol': 'TSLA', 'shortName': 'Tesla, Inc.', 'longName': 'Tesla, Inc.', 'firstTradeDateEpochUtc': 1277818200, 'timeZoneFullName': 'America/New_York', 'timeZoneShortName': 'EST', 'uuid': 'ec367bc4-f92c-397c-ac81-bf7b43cffaf7', 'messageBoardId': 'finmb_27444752', 'gmtOffSetMilliseconds': -18000000, 'currentPrice': 426.5, 'targetHighPrice': 528.0, 'targetLowPrice': 125.0, 'targetMeanPrice': 309.0283, 'targetMedianPrice': 300.0, 'recommendationMean': 2.74468, 'recommendationKey': 'hold', 'numberOfAnalystOpinions': 41, 'totalCash': 33648001024, 'totalCashPerShare': 10.482, 'ebitda': 13244000256, 'totalDebt': 12782999552, 'quickRatio': 1.214, 'currentRatio': 1.844, 'totalRevenue': 97150001152, 'debtToEquity': 18.078, 'revenuePerShare': 30.457, 'returnOnAssets': 0.04759, 'returnOnEquity': 0.20389, 'grossProfits': 17709000704, 'freeCashflow': 676625024, 'operatingCashflow': 14478999552, 'earningsGrowth': 0.17, 'revenueGrowth': 0.078, 'grossMargins': 0.18229, 'ebitdaMargins': 0.13633001, 'operatingMargins': 0.107889995, 'financialCurrency': 'USD', 'trailingPegRatio': 5.1022}
                                                           2023-12-31  \
    Tax Effect Of Unusual Items                                   0.0   
    Tax Rate For Calcs                                           0.21   
    Normalized EBITDA                                   14796000000.0   
    Total Unusual Items                                           0.0   
    Total Unusual Items Excluding Goodwill                        0.0   
    Net Income From Continuing Operation Net Minori...  14999000000.0   
    Reconciled Depreciation                              4667000000.0   
    Reconciled Cost Of Revenue                          79113000000.0   
    EBITDA                                              14796000000.0   
    EBIT                                                10129000000.0   
    Net Interest Income                                   910000000.0   
    Interest Expense                                      156000000.0   
    Interest Income                                      1066000000.0   
    Normalized Income                                   14999000000.0   
    Net Income From Continuing And Discontinued Ope...  14999000000.0   
    Total Expenses                                      87882000000.0   
    Rent Expense Supplemental                            1268000000.0   
    Total Operating Income As Reported                   8891000000.0   
    Diluted Average Shares                               3485000000.0   
    Basic Average Shares                                 3174000000.0   
    Diluted EPS                                                   4.3   
    Basic EPS                                                    4.73   
    Diluted NI Availto Com Stockholders                 14999000000.0   
    Average Dilution Earnings                                     0.0   
    Net Income Common Stockholders                      14999000000.0   
    Otherunder Preferred Stock Dividend                           NaN   
    Net Income                                          14999000000.0   
    Minority Interests                                     25000000.0   
    Net Income Including Noncontrolling Interests       14974000000.0   
    Net Income Continuous Operations                    14974000000.0   
    Tax Provision                                       -5001000000.0   
    Pretax Income                                        9973000000.0   
    Other Income Expense                                  172000000.0   
    Other Non Operating Income Expenses                   172000000.0   
    Special Income Charges                                        0.0   
    Restructuring And Mergern Acquisition                         0.0   
    Net Non Operating Interest Income Expense             910000000.0   
    Interest Expense Non Operating                        156000000.0   
    Interest Income Non Operating                        1066000000.0   
    Operating Income                                     8891000000.0   
    Operating Expense                                    8769000000.0   
    Research And Development                             3969000000.0   
    Selling General And Administration                   4800000000.0   
    Gross Profit                                        17660000000.0   
    Cost Of Revenue                                     79113000000.0   
    Total Revenue                                       96773000000.0   
    Operating Revenue                                   96773000000.0   
    
                                                           2022-12-31  \
    Tax Effect Of Unusual Items                           -14080000.0   
    Tax Rate For Calcs                                           0.08   
    Normalized EBITDA                                   17833000000.0   
    Total Unusual Items                                  -176000000.0   
    Total Unusual Items Excluding Goodwill               -176000000.0   
    Net Income From Continuing Operation Net Minori...  12583000000.0   
    Reconciled Depreciation                              3747000000.0   
    Reconciled Cost Of Revenue                          60609000000.0   
    EBITDA                                              17657000000.0   
    EBIT                                                13910000000.0   
    Net Interest Income                                   106000000.0   
    Interest Expense                                      191000000.0   
    Interest Income                                       297000000.0   
    Normalized Income                                   12744920000.0   
    Net Income From Continuing And Discontinued Ope...  12583000000.0   
    Total Expenses                                      67630000000.0   
    Rent Expense Supplemental                            1509000000.0   
    Total Operating Income As Reported                  13656000000.0   
    Diluted Average Shares                               3475000000.0   
    Basic Average Shares                                 3130000000.0   
    Diluted EPS                                                  3.62   
    Basic EPS                                                    4.02   
    Diluted NI Availto Com Stockholders                 12584000000.0   
    Average Dilution Earnings                               1000000.0   
    Net Income Common Stockholders                      12583000000.0   
    Otherunder Preferred Stock Dividend                           NaN   
    Net Income                                          12583000000.0   
    Minority Interests                                     -4000000.0   
    Net Income Including Noncontrolling Interests       12587000000.0   
    Net Income Continuous Operations                    12587000000.0   
    Tax Provision                                        1132000000.0   
    Pretax Income                                       13719000000.0   
    Other Income Expense                                 -219000000.0   
    Other Non Operating Income Expenses                   -43000000.0   
    Special Income Charges                               -176000000.0   
    Restructuring And Mergern Acquisition                 176000000.0   
    Net Non Operating Interest Income Expense             106000000.0   
    Interest Expense Non Operating                        191000000.0   
    Interest Income Non Operating                         297000000.0   
    Operating Income                                    13832000000.0   
    Operating Expense                                    7021000000.0   
    Research And Development                             3075000000.0   
    Selling General And Administration                   3946000000.0   
    Gross Profit                                        20853000000.0   
    Cost Of Revenue                                     60609000000.0   
    Total Revenue                                       81462000000.0   
    Operating Revenue                                   81462000000.0   
    
                                                           2021-12-31  \
    Tax Effect Of Unusual Items                             2970000.0   
    Tax Rate For Calcs                                           0.11   
    Normalized EBITDA                                    9598000000.0   
    Total Unusual Items                                    27000000.0   
    Total Unusual Items Excluding Goodwill                 27000000.0   
    Net Income From Continuing Operation Net Minori...   5524000000.0   
    Reconciled Depreciation                              2911000000.0   
    Reconciled Cost Of Revenue                          40217000000.0   
    EBITDA                                               9625000000.0   
    EBIT                                                 6714000000.0   
    Net Interest Income                                  -315000000.0   
    Interest Expense                                      371000000.0   
    Interest Income                                        56000000.0   
    Normalized Income                                    5499970000.0   
    Net Income From Continuing And Discontinued Ope...   5524000000.0   
    Total Expenses                                      47327000000.0   
    Rent Expense Supplemental                             978000000.0   
    Total Operating Income As Reported                   6523000000.0   
    Diluted Average Shares                               3386000000.0   
    Basic Average Shares                                 2959000000.0   
    Diluted EPS                                                  1.63   
    Basic EPS                                                    1.87   
    Diluted NI Availto Com Stockholders                  5533000000.0   
    Average Dilution Earnings                               9000000.0   
    Net Income Common Stockholders                       5524000000.0   
    Otherunder Preferred Stock Dividend                    -5000000.0   
    Net Income                                           5524000000.0   
    Minority Interests                                   -120000000.0   
    Net Income Including Noncontrolling Interests        5644000000.0   
    Net Income Continuous Operations                     5644000000.0   
    Tax Provision                                         699000000.0   
    Pretax Income                                        6343000000.0   
    Other Income Expense                                  162000000.0   
    Other Non Operating Income Expenses                   135000000.0   
    Special Income Charges                                 27000000.0   
    Restructuring And Mergern Acquisition                 -27000000.0   
    Net Non Operating Interest Income Expense            -315000000.0   
    Interest Expense Non Operating                        371000000.0   
    Interest Income Non Operating                          56000000.0   
    Operating Income                                     6496000000.0   
    Operating Expense                                    7110000000.0   
    Research And Development                             2593000000.0   
    Selling General And Administration                   4517000000.0   
    Gross Profit                                        13606000000.0   
    Cost Of Revenue                                     40217000000.0   
    Total Revenue                                       53823000000.0   
    Operating Revenue                                   53823000000.0   
    
                                                           2020-12-31  
    Tax Effect Of Unusual Items                                   0.0  
    Tax Rate For Calcs                                           0.25  
    Normalized EBITDA                                    4224000000.0  
    Total Unusual Items                                           0.0  
    Total Unusual Items Excluding Goodwill                        0.0  
    Net Income From Continuing Operation Net Minori...    721000000.0  
    Reconciled Depreciation                              2322000000.0  
    Reconciled Cost Of Revenue                          24906000000.0  
    EBITDA                                               4224000000.0  
    EBIT                                                 1902000000.0  
    Net Interest Income                                  -718000000.0  
    Interest Expense                                      748000000.0  
    Interest Income                                        30000000.0  
    Normalized Income                                     721000000.0  
    Net Income From Continuing And Discontinued Ope...    721000000.0  
    Total Expenses                                      29542000000.0  
    Rent Expense Supplemental                             563000000.0  
    Total Operating Income As Reported                  -1994000000.0  
    Diluted Average Shares                               3249000000.0  
    Basic Average Shares                                 2799000000.0  
    Diluted EPS                                              0.213333  
    Basic EPS                                                0.246667  
    Diluted NI Availto Com Stockholders                   690000000.0  
    Average Dilution Earnings                                     0.0  
    Net Income Common Stockholders                        690000000.0  
    Otherunder Preferred Stock Dividend                    31000000.0  
    Net Income                                            721000000.0  
    Minority Interests                                   -141000000.0  
    Net Income Including Noncontrolling Interests         862000000.0  
    Net Income Continuous Operations                      862000000.0  
    Tax Provision                                         292000000.0  
    Pretax Income                                        1154000000.0  
    Other Income Expense                                 -122000000.0  
    Other Non Operating Income Expenses                  -122000000.0  
    Special Income Charges                                        0.0  
    Restructuring And Mergern Acquisition                         0.0  
    Net Non Operating Interest Income Expense            -718000000.0  
    Interest Expense Non Operating                        748000000.0  
    Interest Income Non Operating                          30000000.0  
    Operating Income                                     1994000000.0  
    Operating Expense                                    4636000000.0  
    Research And Development                             1491000000.0  
    Selling General And Administration                   3145000000.0  
    Gross Profit                                         6630000000.0  
    Cost Of Revenue                                     24906000000.0  
    Total Revenue                                       31536000000.0  
    Operating Revenue                                   31536000000.0  


Using the ticker object and the function `history` extract stock information and save it in a dataframe named `tesla_data`. Set the `period` parameter to ` "max" ` so we get information for the maximum amount of time.



```python
historical_data = tesla.history(period="max")  # Last 1 month of data
print(historical_data)
```

                                     Open        High         Low       Close  \
    Date                                                                        
    2010-06-29 00:00:00-04:00    1.266667    1.666667    1.169333    1.592667   
    2010-06-30 00:00:00-04:00    1.719333    2.028000    1.553333    1.588667   
    2010-07-01 00:00:00-04:00    1.666667    1.728000    1.351333    1.464000   
    2010-07-02 00:00:00-04:00    1.533333    1.540000    1.247333    1.280000   
    2010-07-06 00:00:00-04:00    1.333333    1.333333    1.055333    1.074000   
    ...                               ...         ...         ...         ...   
    2025-01-13 00:00:00-05:00  383.209991  403.790009  380.070007  403.309998   
    2025-01-14 00:00:00-05:00  414.339996  422.640015  394.540009  396.359985   
    2025-01-15 00:00:00-05:00  409.899994  429.799988  405.660004  428.220001   
    2025-01-16 00:00:00-05:00  423.489990  424.000000  409.130005  413.820007   
    2025-01-17 00:00:00-05:00  421.500000  439.739990  419.750000  426.500000   
    
                                  Volume  Dividends  Stock Splits  
    Date                                                           
    2010-06-29 00:00:00-04:00  281494500        0.0           0.0  
    2010-06-30 00:00:00-04:00  257806500        0.0           0.0  
    2010-07-01 00:00:00-04:00  123282000        0.0           0.0  
    2010-07-02 00:00:00-04:00   77097000        0.0           0.0  
    2010-07-06 00:00:00-04:00  103003500        0.0           0.0  
    ...                              ...        ...           ...  
    2025-01-13 00:00:00-05:00   67580500        0.0           0.0  
    2025-01-14 00:00:00-05:00   84565000        0.0           0.0  
    2025-01-15 00:00:00-05:00   81375500        0.0           0.0  
    2025-01-16 00:00:00-05:00   68335200        0.0           0.0  
    2025-01-17 00:00:00-05:00   94504200        0.0           0.0  
    
    [3663 rows x 7 columns]


**Reset the index** using the `reset_index(inplace=True)` function on the tesla_data DataFrame and display the first five rows of the `tesla_data` dataframe using the `head` function. Take a screenshot of the results and code from the beginning of Question 1 to the results below.



```python
# Install the yfinance library if you don't have it
# !pip install yfinance

import yfinance as yf

# Create a Ticker object for Tesla (TSLA)
tesla = yf.Ticker("TSLA")

# Extract historical data with period set to "max"
tesla_data = tesla.history(period="max")

# Reset the index of the DataFrame
tesla_data.reset_index(inplace=True)

# Display the first five rows of the DataFrame
print(tesla_data.head())
```

                           Date      Open      High       Low     Close  \
    0 2010-06-29 00:00:00-04:00  1.266667  1.666667  1.169333  1.592667   
    1 2010-06-30 00:00:00-04:00  1.719333  2.028000  1.553333  1.588667   
    2 2010-07-01 00:00:00-04:00  1.666667  1.728000  1.351333  1.464000   
    3 2010-07-02 00:00:00-04:00  1.533333  1.540000  1.247333  1.280000   
    4 2010-07-06 00:00:00-04:00  1.333333  1.333333  1.055333  1.074000   
    
          Volume  Dividends  Stock Splits  
    0  281494500        0.0           0.0  
    1  257806500        0.0           0.0  
    2  123282000        0.0           0.0  
    3   77097000        0.0           0.0  
    4  103003500        0.0           0.0  


## Question 2: Use Webscraping to Extract Tesla Revenue Data


Use the `requests` library to download the webpage https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-PY0220EN-SkillsNetwork/labs/project/revenue.htm Save the text of the response as a variable named `html_data`.



```python
# Install the requests library if you don't have it
# !pip install requests

import requests

# URL of the webpage
url = "https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-PY0220EN-SkillsNetwork/labs/project/revenue.htm"

# Send a GET request to the URL
response = requests.get(url)

# Check if the request was successful (status code 200)
if response.status_code == 200:
    # Save the text content of the response to html_data
    html_data = response.text
    print("Webpage downloaded successfully!")
else:
    print(f"Failed to download webpage. Status code: {response.status_code}")
```

    Webpage downloaded successfully!


Parse the html data using `beautiful_soup` using parser i.e `html5lib` or `html.parser`.



```python
from bs4 import BeautifulSoup

# Parse the HTML content using BeautifulSoup
soup = BeautifulSoup(html_data, "html.parser")

# Display the title of the webpage
print("Title of the webpage:", soup.title.text)
```

    Title of the webpage: Tesla Revenue 2010-2022 | TSLA | MacroTrends


Using `BeautifulSoup` or the `read_html` function extract the table with `Tesla Revenue` and store it into a dataframe named `tesla_revenue`. The dataframe should have columns `Date` and `Revenue`.


<details><summary>Step-by-step instructions</summary>

```

Here are the step-by-step instructions:

1. Create an Empty DataFrame
2. Find the Relevant Table
3. Check for the Tesla Quarterly Revenue Table
4. Iterate Through Rows in the Table Body
5. Extract Data from Columns
6. Append Data to the DataFrame

```
</details>


<details><summary>Click here if you need help locating the table</summary>

```
    
Below is the code to isolate the table, you will now need to loop through the rows and columns like in the previous lab
    
soup.find_all("tbody")[1]
    
If you want to use the read_html function the table is located at index 1

We are focusing on quarterly revenue in the lab.
```

</details>



```python
import pandas as pd

# Use pandas.read_html to extract all tables from the HTML content
tables = pd.read_html(html_data)

# The table we want is the first one (index 0)
tesla_revenue = tables[0]

# Rename the columns to "Date" and "Revenue"
tesla_revenue.columns = ["Date", "Revenue"]

# Display the first few rows of the DataFrame
print(tesla_revenue.head())
```

       Date  Revenue
    0  2021  $53,823
    1  2020  $31,536
    2  2019  $24,578
    3  2018  $21,461
    4  2017  $11,759


Execute the following line to remove the comma and dollar sign from the `Revenue` column. 



```python
tesla_revenue["Revenue"] = tesla_revenue['Revenue'].str.replace(',|\$',"")
```

Execute the following lines to remove an null or empty strings in the Revenue column.



```python
tesla_revenue.dropna(inplace=True)

tesla_revenue = tesla_revenue[tesla_revenue['Revenue'] != ""]
```

Display the last 5 row of the `tesla_revenue` dataframe using the `tail` function. Take a screenshot of the results.



```python
import pandas as pd

# Use pandas.read_html to extract all tables from the HTML content
tables = pd.read_html(html_data)

# The table we want is the first one (index 0)
tesla_revenue = tables[0]

# Rename the columns to "Date" and "Revenue"
tesla_revenue.columns = ["Date", "Revenue"]

# Display the last 5 rows of the DataFrame
print(tesla_revenue.tail())
```

        Date Revenue
    8   2013  $2,013
    9   2012    $413
    10  2011    $204
    11  2010    $117
    12  2009    $112


## Question 3: Use yfinance to Extract Stock Data


Using the `Ticker` function enter the ticker symbol of the stock we want to extract data on to create a ticker object. The stock is GameStop and its ticker symbol is `GME`.



```python
# Install the yfinance library if you don't have it
# !pip install yfinance

import yfinance as yf

# Create a Ticker object for GameStop (GME)
gme = yf.Ticker("GME")

# Extract data (e.g., historical prices, info, financials)
# Example: Get historical market data
historical_data = gme.history(period="1mo")  # Last 1 month of data
print(historical_data)

# Example: Get general information about the stock
info = gme.info
print(info)

# Example: Get financials
financials = gme.financials
print(financials)
```

                                    Open       High        Low      Close  \
    Date                                                                    
    2024-12-18 00:00:00-05:00  31.100000  31.700001  28.340000  28.549999   
    2024-12-19 00:00:00-05:00  29.160000  30.600000  28.820000  29.000000   
    2024-12-20 00:00:00-05:00  28.540001  30.520000  28.309999  29.820000   
    2024-12-23 00:00:00-05:00  29.820000  31.110001  29.780001  30.900000   
    2024-12-24 00:00:00-05:00  31.000000  31.590000  30.580000  31.139999   
    2024-12-26 00:00:00-05:00  32.619999  34.369999  31.600000  32.990002   
    2024-12-27 00:00:00-05:00  32.389999  33.049999  30.730000  32.200001   
    2024-12-30 00:00:00-05:00  31.799999  32.880001  31.610001  32.009998   
    2024-12-31 00:00:00-05:00  32.060001  32.439999  31.100000  31.340000   
    2025-01-02 00:00:00-05:00  31.840000  32.049999  30.370001  30.660000   
    2025-01-03 00:00:00-05:00  30.799999  32.139999  30.570000  31.650000   
    2025-01-06 00:00:00-05:00  31.700001  33.490002  30.760000  32.820000   
    2025-01-07 00:00:00-05:00  32.799999  34.400002  31.709999  33.369999   
    2025-01-08 00:00:00-05:00  32.970001  33.369999  32.410000  32.959999   
    2025-01-10 00:00:00-05:00  32.500000  32.939999  31.400000  32.310001   
    2025-01-13 00:00:00-05:00  31.600000  31.799999  30.900000  31.020000   
    2025-01-14 00:00:00-05:00  31.260000  31.680000  27.559999  27.879999   
    2025-01-15 00:00:00-05:00  28.900000  29.330000  27.840000  27.959999   
    2025-01-16 00:00:00-05:00  27.940001  28.139999  27.410000  27.719999   
    2025-01-17 00:00:00-05:00  27.610001  28.790001  27.020000  27.510000   
    
                                 Volume  Dividends  Stock Splits  
    Date                                                          
    2024-12-18 00:00:00-05:00  13947300        0.0           0.0  
    2024-12-19 00:00:00-05:00  10338200        0.0           0.0  
    2024-12-20 00:00:00-05:00  19606700        0.0           0.0  
    2024-12-23 00:00:00-05:00   8226500        0.0           0.0  
    2024-12-24 00:00:00-05:00   5523500        0.0           0.0  
    2024-12-26 00:00:00-05:00  20432900        0.0           0.0  
    2024-12-27 00:00:00-05:00  10141700        0.0           0.0  
    2024-12-30 00:00:00-05:00   9593100        0.0           0.0  
    2024-12-31 00:00:00-05:00   7395300        0.0           0.0  
    2025-01-02 00:00:00-05:00   7979700        0.0           0.0  
    2025-01-03 00:00:00-05:00   7461800        0.0           0.0  
    2025-01-06 00:00:00-05:00  12609400        0.0           0.0  
    2025-01-07 00:00:00-05:00  13360700        0.0           0.0  
    2025-01-08 00:00:00-05:00   6320000        0.0           0.0  
    2025-01-10 00:00:00-05:00   7068200        0.0           0.0  
    2025-01-13 00:00:00-05:00   5567000        0.0           0.0  
    2025-01-14 00:00:00-05:00  11796600        0.0           0.0  
    2025-01-15 00:00:00-05:00   6025400        0.0           0.0  
    2025-01-16 00:00:00-05:00   4432000        0.0           0.0  
    2025-01-17 00:00:00-05:00   8883200        0.0           0.0  
    {'address1': '625 Westport Parkway', 'city': 'Grapevine', 'state': 'TX', 'zip': '76051', 'country': 'United States', 'phone': '817 424 2000', 'website': 'https://www.gamestop.com', 'industry': 'Specialty Retail', 'industryKey': 'specialty-retail', 'industryDisp': 'Specialty Retail', 'sector': 'Consumer Cyclical', 'sectorKey': 'consumer-cyclical', 'sectorDisp': 'Consumer Cyclical', 'longBusinessSummary': 'GameStop Corp., a specialty retailer, provides games and entertainment products through its stores and ecommerce platforms in the United States, Canada, Australia, and Europe. The company sells new and pre-owned gaming platforms; accessories, such as controllers, gaming headsets, and virtual reality products; new and pre-owned gaming software; and in-game digital currency, digital downloadable content, and full-game downloads. It sells collectibles comprising apparel, toys, trading cards, gadgets, and other retail products for pop culture and technology enthusiasts, as well as engages in the digital asset wallet and NFT marketplace activities. The company operates stores and ecommerce sites under the GameStop, EB Games, and Micromania brands; and pop culture themed stores that sell collectibles, apparel, gadgets, electronics, toys, and other retail products under the Zing Pop Culture brand, as well as offers Game Informer magazine, a print and digital gaming publication. The company was formerly known as GSC Holdings Corp. GameStop Corp. was founded in 1996 and is headquartered in Grapevine, Texas.', 'fullTimeEmployees': 8000, 'companyOfficers': [{'maxAge': 1, 'name': 'Mr. Ryan  Cohen', 'age': 37, 'title': 'President, CEO & Executive Chairman', 'yearBorn': 1986, 'fiscalYear': 2023, 'exercisedValue': 0, 'unexercisedValue': 0}, {'maxAge': 1, 'name': 'Mr. Daniel William Moore', 'age': 40, 'title': 'Principal Accounting Officer & Principal Financial Officer', 'yearBorn': 1983, 'fiscalYear': 2023, 'totalPay': 277711, 'exercisedValue': 0, 'unexercisedValue': 0}, {'maxAge': 1, 'name': 'Mr. Mark Haymond Robinson', 'age': 45, 'title': 'General Counsel & Secretary', 'yearBorn': 1978, 'fiscalYear': 2023, 'totalPay': 337657, 'exercisedValue': 0, 'unexercisedValue': 0}], 'auditRisk': 8, 'boardRisk': 6, 'compensationRisk': 7, 'shareHolderRightsRisk': 3, 'overallRisk': 5, 'governanceEpochDate': 1733011200, 'compensationAsOfEpochDate': 1703980800, 'irWebsite': 'http://phx.corporate-ir.net/phoenix.zhtml?c=130125&p=irol-irhome', 'maxAge': 86400, 'priceHint': 2, 'previousClose': 27.72, 'open': 27.61, 'dayLow': 27.02, 'dayHigh': 28.7899, 'regularMarketPreviousClose': 27.72, 'regularMarketOpen': 27.61, 'regularMarketDayLow': 27.02, 'regularMarketDayHigh': 28.7899, 'exDividendDate': 1552521600, 'fiveYearAvgDividendYield': 9.52, 'beta': -0.098, 'trailingPE': 137.55, 'forwardPE': 'Infinity', 'volume': 8617328, 'regularMarketVolume': 8617328, 'averageVolume': 11350826, 'averageVolume10days': 8352430, 'averageDailyVolume10Day': 8352430, 'bid': 27.43, 'ask': 27.49, 'bidSize': 1300, 'askSize': 1000, 'marketCap': 12291468288, 'fiftyTwoWeekLow': 9.95, 'fiftyTwoWeekHigh': 64.83, 'priceToSalesTrailing12Months': 2.7002347, 'fiftyDayAverage': 28.8314, 'twoHundredDayAverage': 23.33215, 'currency': 'USD', 'enterpriseValue': 7815203328, 'profitMargins': 0.00934, 'floatShares': 390217891, 'sharesOutstanding': 446800000, 'sharesShort': 32404004, 'sharesShortPriorMonth': 35943712, 'sharesShortPreviousMonthDate': 1730332800, 'dateShortInterest': 1732838400, 'sharesPercentSharesOut': 0.0726, 'heldPercentInsiders': 0.08495, 'heldPercentInstitutions': 0.28699, 'shortRatio': 2.6, 'shortPercentOfFloat': 0.087, 'impliedSharesOutstanding': 450211008, 'bookValue': 4.379, 'priceToBook': 6.282256, 'lastFiscalYearEnd': 1706918400, 'nextFiscalYearEnd': 1738540800, 'mostRecentQuarter': 1722643200, 'netIncomeToCommon': 42500000, 'trailingEps': 0.2, 'forwardEps': -0.01, 'lastSplitFactor': '4:1', 'lastSplitDate': 1658448000, 'enterpriseToRevenue': 1.717, 'enterpriseToEbitda': 165.576, '52WeekChange': 0.8463087, 'SandP52WeekChange': 0.23631513, 'lastDividendValue': 0.095, 'lastDividendDate': 1552521600, 'exchange': 'NYQ', 'quoteType': 'EQUITY', 'symbol': 'GME', 'underlyingSymbol': 'GME', 'shortName': 'GameStop Corporation', 'longName': 'GameStop Corp.', 'firstTradeDateEpochUtc': 1013610600, 'timeZoneFullName': 'America/New_York', 'timeZoneShortName': 'EST', 'uuid': '8ded85bd-8171-3e2e-afa6-c81272285147', 'messageBoardId': 'finmb_1342560', 'gmtOffSetMilliseconds': -18000000, 'currentPrice': 27.51, 'targetHighPrice': 10.0, 'targetLowPrice': 10.0, 'targetMeanPrice': 10.0, 'targetMedianPrice': 10.0, 'recommendationKey': 'none', 'numberOfAnalystOpinions': 1, 'totalCash': 4204199936, 'totalCashPerShare': 9.857, 'ebitda': 47200000, 'totalDebt': 533500000, 'quickRatio': 5.442, 'currentRatio': 6.233, 'totalRevenue': 4552000000, 'debtToEquity': 12.171, 'revenuePerShare': 13.97, 'returnOnAssets': 0.00043000001, 'returnOnEquity': 0.015039999, 'grossProfits': 1194300032, 'freeCashflow': -93387504, 'operatingCashflow': -33100000, 'revenueGrowth': -0.314, 'grossMargins': 0.26237, 'ebitdaMargins': 0.010369999, 'operatingMargins': -0.03558, 'financialCurrency': 'USD', 'trailingPegRatio': None}
                                                          2024-01-31  \
    Tax Effect Of Unusual Items                           -1008000.0   
    Tax Rate For Calcs                                          0.21   
    Normalized EBITDA                                     31300000.0   
    Total Unusual Items                                   -4800000.0   
    Total Unusual Items Excluding Goodwill                -4800000.0   
    Net Income From Continuing Operation Net Minori...     6700000.0   
    Reconciled Depreciation                               56200000.0   
    Reconciled Cost Of Revenue                          3978600000.0   
    EBITDA                                                26500000.0   
    EBIT                                                 -29700000.0   
    Net Interest Income                                   49500000.0   
    Interest Expense                                             NaN   
    Interest Income                                       49500000.0   
    Normalized Income                                     10492000.0   
    Net Income From Continuing And Discontinued Ope...     6700000.0   
    Total Expenses                                      5302500000.0   
    Total Operating Income As Reported                   -34500000.0   
    Diluted Average Shares                               305200000.0   
    Basic Average Shares                                 305100000.0   
    Diluted EPS                                                 0.02   
    Basic EPS                                                   0.02   
    Diluted NI Availto Com Stockholders                    6700000.0   
    Net Income Common Stockholders                         6700000.0   
    Net Income                                             6700000.0   
    Net Income Including Noncontrolling Interests          6700000.0   
    Net Income Discontinuous Operations                          NaN   
    Net Income Continuous Operations                       6700000.0   
    Tax Provision                                          6400000.0   
    Pretax Income                                         13100000.0   
    Other Income Expense                                  -6700000.0   
    Other Non Operating Income Expenses                   -1900000.0   
    Special Income Charges                                -4800000.0   
    Gain On Sale Of Ppe                                          NaN   
    Write Off                                              4800000.0   
    Impairment Of Capital Assets                                 NaN   
    Net Non Operating Interest Income Expense             49500000.0   
    Total Other Finance Cost                             -49500000.0   
    Interest Expense Non Operating                               NaN   
    Interest Income Non Operating                         49500000.0   
    Operating Income                                     -29700000.0   
    Operating Expense                                   1323900000.0   
    Selling General And Administration                  1323900000.0   
    Gross Profit                                        1294200000.0   
    Cost Of Revenue                                     3978600000.0   
    Total Revenue                                       5272800000.0   
    Operating Revenue                                   5272800000.0   
    
                                                          2023-01-31  \
    Tax Effect Of Unusual Items                            -567000.0   
    Tax Rate For Calcs                                          0.21   
    Normalized EBITDA                                   -244500000.0   
    Total Unusual Items                                   -2700000.0   
    Total Unusual Items Excluding Goodwill                -2700000.0   
    Net Income From Continuing Operation Net Minori...  -313100000.0   
    Reconciled Depreciation                               61700000.0   
    Reconciled Cost Of Revenue                          4555100000.0   
    EBITDA                                              -247200000.0   
    EBIT                                                -308900000.0   
    Net Interest Income                                    9500000.0   
    Interest Expense                                             NaN   
    Interest Income                                        9500000.0   
    Normalized Income                                   -310967000.0   
    Net Income From Continuing And Discontinued Ope...  -313100000.0   
    Total Expenses                                      6236100000.0   
    Total Operating Income As Reported                  -311600000.0   
    Diluted Average Shares                               304200000.0   
    Basic Average Shares                                 304200000.0   
    Diluted EPS                                                -1.03   
    Basic EPS                                                  -1.03   
    Diluted NI Availto Com Stockholders                 -313100000.0   
    Net Income Common Stockholders                      -313100000.0   
    Net Income                                          -313100000.0   
    Net Income Including Noncontrolling Interests       -313100000.0   
    Net Income Discontinuous Operations                          0.0   
    Net Income Continuous Operations                    -313100000.0   
    Tax Provision                                         11000000.0   
    Pretax Income                                       -302100000.0   
    Other Income Expense                                  -2700000.0   
    Other Non Operating Income Expenses                          NaN   
    Special Income Charges                                -2700000.0   
    Gain On Sale Of Ppe                                          0.0   
    Write Off                                              2700000.0   
    Impairment Of Capital Assets                           2700000.0   
    Net Non Operating Interest Income Expense              9500000.0   
    Total Other Finance Cost                              -9500000.0   
    Interest Expense Non Operating                               NaN   
    Interest Income Non Operating                          9500000.0   
    Operating Income                                    -308900000.0   
    Operating Expense                                   1681000000.0   
    Selling General And Administration                  1681000000.0   
    Gross Profit                                        1372100000.0   
    Cost Of Revenue                                     4555100000.0   
    Total Revenue                                       5927200000.0   
    Operating Revenue                                   5927200000.0   
    
                                                          2022-01-31  \
    Tax Effect Of Unusual Items                            -241200.0   
    Tax Rate For Calcs                                         0.036   
    Normalized EBITDA                                   -277900000.0   
    Total Unusual Items                                   -6700000.0   
    Total Unusual Items Excluding Goodwill                -6700000.0   
    Net Income From Continuing Operation Net Minori...  -381300000.0   
    Reconciled Depreciation                               77200000.0   
    Reconciled Cost Of Revenue                          4662900000.0   
    EBITDA                                              -284600000.0   
    EBIT                                                -361800000.0   
    Net Interest Income                                  -26900000.0   
    Interest Expense                                      26900000.0   
    Interest Income                                      -26900000.0   
    Normalized Income                                   -374841200.0   
    Net Income From Continuing And Discontinued Ope...  -381300000.0   
    Total Expenses                                      6372500000.0   
    Total Operating Income As Reported                  -368500000.0   
    Diluted Average Shares                               290400000.0   
    Basic Average Shares                                 290400000.0   
    Diluted EPS                                                -1.31   
    Basic EPS                                                  -1.31   
    Diluted NI Availto Com Stockholders                 -381300000.0   
    Net Income Common Stockholders                      -381300000.0   
    Net Income                                          -381300000.0   
    Net Income Including Noncontrolling Interests       -381300000.0   
    Net Income Discontinuous Operations                          0.0   
    Net Income Continuous Operations                    -381300000.0   
    Tax Provision                                        -14100000.0   
    Pretax Income                                       -395400000.0   
    Other Income Expense                                  -6700000.0   
    Other Non Operating Income Expenses                          NaN   
    Special Income Charges                                -6700000.0   
    Gain On Sale Of Ppe                                          0.0   
    Write Off                                              6700000.0   
    Impairment Of Capital Assets                           6700000.0   
    Net Non Operating Interest Income Expense            -26900000.0   
    Total Other Finance Cost                              26900000.0   
    Interest Expense Non Operating                        26900000.0   
    Interest Income Non Operating                        -26900000.0   
    Operating Income                                    -361800000.0   
    Operating Expense                                   1709600000.0   
    Selling General And Administration                  1709600000.0   
    Gross Profit                                        1347800000.0   
    Cost Of Revenue                                     4662900000.0   
    Total Revenue                                       6010700000.0   
    Operating Revenue                                   6010700000.0   
    
                                                          2021-01-31   2020-01-31  
    Tax Effect Of Unusual Items                            3464500.0          NaN  
    Tax Rate For Calcs                                         0.205          NaN  
    Normalized EBITDA                                   -190900000.0          NaN  
    Total Unusual Items                                   16900000.0          NaN  
    Total Unusual Items Excluding Goodwill                16900000.0          NaN  
    Net Income From Continuing Operation Net Minori...  -214600000.0          NaN  
    Reconciled Depreciation                               80700000.0          NaN  
    Reconciled Cost Of Revenue                          3830300000.0          NaN  
    EBITDA                                              -174000000.0          NaN  
    EBIT                                                -254700000.0          NaN  
    Net Interest Income                                  -32100000.0          NaN  
    Interest Expense                                      34000000.0   27200000.0  
    Interest Income                                      -32100000.0          NaN  
    Normalized Income                                   -228035500.0          NaN  
    Net Income From Continuing And Discontinued Ope...  -215300000.0          NaN  
    Total Expenses                                      5344500000.0          NaN  
    Total Operating Income As Reported                  -237800000.0          NaN  
    Diluted Average Shares                               260000000.0          NaN  
    Basic Average Shares                                 260000000.0          NaN  
    Diluted EPS                                              -0.8275          NaN  
    Basic EPS                                                -0.8275          NaN  
    Diluted NI Availto Com Stockholders                 -215300000.0          NaN  
    Net Income Common Stockholders                      -215300000.0          NaN  
    Net Income                                          -215300000.0          NaN  
    Net Income Including Noncontrolling Interests       -215300000.0          NaN  
    Net Income Discontinuous Operations                    -700000.0   -6500000.0  
    Net Income Continuous Operations                    -214600000.0          NaN  
    Tax Provision                                        -55300000.0          NaN  
    Pretax Income                                       -269900000.0          NaN  
    Other Income Expense                                  16900000.0          NaN  
    Other Non Operating Income Expenses                          NaN          NaN  
    Special Income Charges                                16900000.0          NaN  
    Gain On Sale Of Ppe                                   32400000.0          0.0  
    Write Off                                             15500000.0          NaN  
    Impairment Of Capital Assets                          15500000.0  385600000.0  
    Net Non Operating Interest Income Expense            -32100000.0          NaN  
    Total Other Finance Cost                              32100000.0          NaN  
    Interest Expense Non Operating                        34000000.0   27200000.0  
    Interest Income Non Operating                        -32100000.0          NaN  
    Operating Income                                    -254700000.0          NaN  
    Operating Expense                                   1514200000.0          NaN  
    Selling General And Administration                  1514200000.0          NaN  
    Gross Profit                                        1259500000.0          NaN  
    Cost Of Revenue                                     3830300000.0          NaN  
    Total Revenue                                       5089800000.0          NaN  
    Operating Revenue                                   5089800000.0          NaN  


Using the ticker object and the function `history` extract stock information and save it in a dataframe named `gme_data`. Set the `period` parameter to ` "max" ` so we get information for the maximum amount of time.



```python
historical_data = gme.history(period="max")  # Last 1 month of data
print(historical_data)
```

                                    Open       High        Low      Close  \
    Date                                                                    
    2002-02-13 00:00:00-05:00   1.620129   1.693350   1.603296   1.691667   
    2002-02-14 00:00:00-05:00   1.712707   1.716074   1.670626   1.683250   
    2002-02-15 00:00:00-05:00   1.683250   1.687458   1.658001   1.674834   
    2002-02-19 00:00:00-05:00   1.666418   1.666418   1.578047   1.607504   
    2002-02-20 00:00:00-05:00   1.615920   1.662209   1.603296   1.662209   
    ...                              ...        ...        ...        ...   
    2025-01-13 00:00:00-05:00  31.600000  31.799999  30.900000  31.020000   
    2025-01-14 00:00:00-05:00  31.260000  31.680000  27.559999  27.879999   
    2025-01-15 00:00:00-05:00  28.900000  29.330000  27.840000  27.959999   
    2025-01-16 00:00:00-05:00  27.940001  28.139999  27.410000  27.719999   
    2025-01-17 00:00:00-05:00  27.610001  28.790001  27.020000  27.510000   
    
                                 Volume  Dividends  Stock Splits  
    Date                                                          
    2002-02-13 00:00:00-05:00  76216000        0.0           0.0  
    2002-02-14 00:00:00-05:00  11021600        0.0           0.0  
    2002-02-15 00:00:00-05:00   8389600        0.0           0.0  
    2002-02-19 00:00:00-05:00   7410400        0.0           0.0  
    2002-02-20 00:00:00-05:00   6892800        0.0           0.0  
    ...                             ...        ...           ...  
    2025-01-13 00:00:00-05:00   5567000        0.0           0.0  
    2025-01-14 00:00:00-05:00  11796600        0.0           0.0  
    2025-01-15 00:00:00-05:00   6025400        0.0           0.0  
    2025-01-16 00:00:00-05:00   4432000        0.0           0.0  
    2025-01-17 00:00:00-05:00   8883200        0.0           0.0  
    
    [5771 rows x 7 columns]


**Reset the index** using the `reset_index(inplace=True)` function on the gme_data DataFrame and display the first five rows of the `gme_data` dataframe using the `head` function. Take a screenshot of the results and code from the beginning of Question 3 to the results below.



```python
# Install the yfinance library if you don't have it
# !pip install yfinance

import yfinance as yf

# Create a Ticker object for GameStop (GME)
gme = yf.Ticker("GME")

# Extract historical data with period set to "max"
gme_data = gme.history(period="max")

# Reset the index of the DataFrame
gme_data.reset_index(inplace=True)

# Display the first five rows of the DataFrame
print(gme_data.head())
```

                           Date      Open      High       Low     Close    Volume  \
    0 2002-02-13 00:00:00-05:00  1.620128  1.693350  1.603296  1.691666  76216000   
    1 2002-02-14 00:00:00-05:00  1.712707  1.716073  1.670626  1.683250  11021600   
    2 2002-02-15 00:00:00-05:00  1.683251  1.687459  1.658002  1.674834   8389600   
    3 2002-02-19 00:00:00-05:00  1.666418  1.666418  1.578047  1.607504   7410400   
    4 2002-02-20 00:00:00-05:00  1.615920  1.662210  1.603296  1.662210   6892800   
    
       Dividends  Stock Splits  
    0        0.0           0.0  
    1        0.0           0.0  
    2        0.0           0.0  
    3        0.0           0.0  
    4        0.0           0.0  


## Question 4: Use Webscraping to Extract GME Revenue Data


Use the `requests` library to download the webpage https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-PY0220EN-SkillsNetwork/labs/project/stock.html. Save the text of the response as a variable named `html_data_2`.



```python

import requests

url = "https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-PY0220EN-SkillsNetwork/labs/project/stock.html"

response = requests.get(url)

if response.status_code == 200:
    html_data_2 = response.text
    print("Webpage downloaded successfully!")
else:
    print(f"Failed to download webpage. Status code: {response.status_code}")
```

    Webpage downloaded successfully!


Parse the html data using `beautiful_soup` using parser i.e `html5lib` or `html.parser`.



```python

from bs4 import BeautifulSoup

soup = BeautifulSoup(html_data_2, "html.parser")



print("Title of the webpage:", soup.title.text)

print(soup.prettify())
```

    Title of the webpage: GameStop Revenue 2006-2020 | GME | MacroTrends
    <!DOCTYPE html>
    <!-- saved from url=(0105)https://web.archive.org/web/20200814131437/https://www.macrotrends.net/stocks/charts/GME/gamestop/revenue -->
    <html class="js flexbox canvas canvastext webgl no-touch geolocation postmessage websqldatabase indexeddb hashchange history draganddrop websockets rgba hsla multiplebgs backgroundsize borderimage borderradius boxshadow textshadow opacity cssanimations csscolumns cssgradients cssreflections csstransforms csstransforms3d csstransitions fontface ge


Using `BeautifulSoup` or the `read_html` function extract the table with `GameStop Revenue` and store it into a dataframe named `gme_revenue`. The dataframe should have columns `Date` and `Revenue`. Make sure the comma and dollar sign is removed from the `Revenue` column.


> **Note: Use the method similar to what you did in question 2.**  


<details><summary>Click here if you need help locating the table</summary>

```
    
Below is the code to isolate the table, you will now need to loop through the rows and columns like in the previous lab
    
soup.find_all("tbody")[1]
    
If you want to use the read_html function the table is located at index 1


```

</details>



```python

```

Display the last five rows of the `gme_revenue` dataframe using the `tail` function. Take a screenshot of the results.



```python

```

## Question 5: Plot Tesla Stock Graph


Use the `make_graph` function to graph the Tesla Stock Data, also provide a title for the graph. Note the graph will only show data upto June 2021.


<details><summary>Hint</summary>

```

You just need to invoke the make_graph function with the required parameter to print the graphs.The structure to call the `make_graph` function is `make_graph(tesla_data, tesla_revenue, 'Tesla')`.

```
    
</details>



```python
!pip install matplotlib

import matplotlib.pyplot as plt

def make_graph(data, title):
    data = data[data["Date"] <= "2021-06-30"]
    
    plt.figure(figsize=(10, 6))
    plt.plot(data["Date"], data["Close"], label="Close Price", color="blue")
    
    plt.title(title, fontsize=16)
    plt.xlabel("Date", fontsize=12)
    plt.ylabel("Close Price (USD)", fontsize=12)
    
    plt.xticks(rotation=45)
    
    plt.grid(True)
    
    plt.legend()
    
    plt.tight_layout()
    plt.show()

make_graph(tesla_data, "Tesla Stock Price (Up to June 2021)")
```

    Collecting matplotlib
      Downloading matplotlib-3.10.0-cp312-cp312-manylinux_2_17_x86_64.manylinux2014_x86_64.whl.metadata (11 kB)
    Collecting contourpy>=1.0.1 (from matplotlib)
      Downloading contourpy-1.3.1-cp312-cp312-manylinux_2_17_x86_64.manylinux2014_x86_64.whl.metadata (5.4 kB)
    Collecting cycler>=0.10 (from matplotlib)
      Downloading cycler-0.12.1-py3-none-any.whl.metadata (3.8 kB)
    Collecting fonttools>=4.22.0 (from matplotlib)
      Downloading fonttools-4.55.3-cp312-cp312-manylinux_2_5_x86_64.manylinux1_x86_64.manylinux_2_17_x86_64.manylinux2014_x86_64.whl.metadata (165 kB)
    Collecting kiwisolver>=1.3.1 (from matplotlib)
      Downloading kiwisolver-1.4.8-cp312-cp312-manylinux_2_17_x86_64.manylinux2014_x86_64.whl.metadata (6.2 kB)
    Requirement already satisfied: numpy>=1.23 in /opt/conda/lib/python3.12/site-packages (from matplotlib) (2.2.2)
    Requirement already satisfied: packaging>=20.0 in /opt/conda/lib/python3.12/site-packages (from matplotlib) (24.2)
    Collecting pillow>=8 (from matplotlib)
      Downloading pillow-11.1.0-cp312-cp312-manylinux_2_28_x86_64.whl.metadata (9.1 kB)
    Collecting pyparsing>=2.3.1 (from matplotlib)
      Downloading pyparsing-3.2.1-py3-none-any.whl.metadata (5.0 kB)
    Requirement already satisfied: python-dateutil>=2.7 in /opt/conda/lib/python3.12/site-packages (from matplotlib) (2.9.0.post0)
    Requirement already satisfied: six>=1.5 in /opt/conda/lib/python3.12/site-packages (from python-dateutil>=2.7->matplotlib) (1.17.0)
    Downloading matplotlib-3.10.0-cp312-cp312-manylinux_2_17_x86_64.manylinux2014_x86_64.whl (8.6 MB)
    [2K   [90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━[0m [32m8.6/8.6 MB[0m [31m82.5 MB/s[0m eta [36m0:00:00[0m
    [?25hDownloading contourpy-1.3.1-cp312-cp312-manylinux_2_17_x86_64.manylinux2014_x86_64.whl (323 kB)
    Downloading cycler-0.12.1-py3-none-any.whl (8.3 kB)
    Downloading fonttools-4.55.3-cp312-cp312-manylinux_2_5_x86_64.manylinux1_x86_64.manylinux_2_17_x86_64.manylinux2014_x86_64.whl (4.9 MB)
    [2K   [90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━[0m [32m4.9/4.9 MB[0m [31m53.7 MB/s[0m eta [36m0:00:00[0m
    [?25hDownloading kiwisolver-1.4.8-cp312-cp312-manylinux_2_17_x86_64.manylinux2014_x86_64.whl (1.5 MB)
    [2K   [90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━[0m [32m1.5/1.5 MB[0m [31m43.8 MB/s[0m eta [36m0:00:00[0m
    [?25hDownloading pillow-11.1.0-cp312-cp312-manylinux_2_28_x86_64.whl (4.5 MB)
    [2K   [90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━[0m [32m4.5/4.5 MB[0m [31m70.0 MB/s[0m eta [36m0:00:00[0m
    [?25hDownloading pyparsing-3.2.1-py3-none-any.whl (107 kB)
    Installing collected packages: pyparsing, pillow, kiwisolver, fonttools, cycler, contourpy, matplotlib
    Successfully installed contourpy-1.3.1 cycler-0.12.1 fonttools-4.55.3 kiwisolver-1.4.8 matplotlib-3.10.0 pillow-11.1.0 pyparsing-3.2.1



    
![png](output_56_1.png)
    


## Question 6: Plot GameStop Stock Graph


Use the `make_graph` function to graph the GameStop Stock Data, also provide a title for the graph. The structure to call the `make_graph` function is `make_graph(gme_data, gme_revenue, 'GameStop')`. Note the graph will only show data upto June 2021.


<details><summary>Hint</summary>

```

You just need to invoke the make_graph function with the required parameter to print the graphs.The structure to call the `make_graph` function is `make_graph(gme_data, gme_revenue, 'GameStop')`

```
    
</details>



```python
!pip install yfinance pandas matplotlib

import yfinance as yf
import pandas as pd
import matplotlib.pyplot as plt

gme = yf.Ticker("GME")
gme_data = gme.history(period="max")
gme_data.reset_index(inplace=True)

url = "https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-PY0220EN-SkillsNetwork/labs/project/stock.html"
html_data = pd.read_html(url)
gme_revenue = html_data[0]
gme_revenue.columns = ["Date", "Revenue"]
gme_revenue["Revenue"] = gme_revenue["Revenue"].str.replace("$", "").str.replace(",", "")

gme_data["Date"] = pd.to_datetime(gme_data["Date"])
gme_revenue["Date"] = pd.to_datetime(gme_revenue["Date"])

def make_graph(stock_data, revenue_data, title):
    # Filter data up to June 2021
    stock_data = stock_data[stock_data["Date"] <= "2021-06-30"]
    revenue_data = revenue_data[revenue_data["Date"] <= "2021-06-30"]
    
    fig, ax1 = plt.subplots(figsize=(10, 6))
    
    ax1.plot(stock_data["Date"], stock_data["Close"], label="Close Price", color="blue")
    ax1.set_xlabel("Date", fontsize=12)
    ax1.set_ylabel("Close Price (USD)", fontsize=12)
    ax1.tick_params(axis="y", labelcolor="blue")
    ax1.grid(True)
    
    ax2 = ax1.twinx()
    ax2.plot(revenue_data["Date"], revenue_data["Revenue"], label="Revenue", color="red")
    ax2.set_ylabel("Revenue (USD)", fontsize=12)
    ax2.tick_params(axis="y", labelcolor="red")
    
    plt.title(title, fontsize=16)
    
    plt.xticks(rotation=45)
    
    lines1, labels1 = ax1.get_legend_handles_labels()
    lines2, labels2 = ax2.get_legend_handles_labels()
    ax1.legend(lines1 + lines2, labels1 + labels2, loc="upper left")
    
    plt.tight_layout()
    plt.show()

make_graph(gme_data, gme_revenue, 'GameStop Stock Price and Revenue (Up to June 2021)')
```

    Requirement already satisfied: yfinance in /opt/conda/lib/python3.12/site-packages (0.2.52)
    Requirement already satisfied: pandas in /opt/conda/lib/python3.12/site-packages (2.2.3)
    Requirement already satisfied: matplotlib in /opt/conda/lib/python3.12/site-packages (3.10.0)
    Requirement already satisfied: numpy>=1.16.5 in /opt/conda/lib/python3.12/site-packages (from yfinance) (2.2.2)
    Requirement already satisfied: requests>=2.31 in /opt/conda/lib/python3.12/site-packages (from yfinance) (2.32.3)
    Requirement already satisfied: multitasking>=0.0.7 in /opt/conda/lib/python3.12/site-packages (from yfinance) (0.0.11)
    Requirement already satisfied: lxml>=4.9.1 in /opt/conda/lib/python3.12/site-packages (from yfinance) (5.3.0)
    Requirement already satisfied: platformdirs>=2.0.0 in /opt/conda/lib/python3.12/site-packages (from yfinance) (4.3.6)
    Requirement already satisfied: pytz>=2022.5 in /opt/conda/lib/python3.12/site-packages (from yfinance) (2024.2)
    Requirement already satisfied: frozendict>=2.3.4 in /opt/conda/lib/python3.12/site-packages (from yfinance) (2.4.6)
    Requirement already satisfied: peewee>=3.16.2 in /opt/conda/lib/python3.12/site-packages (from yfinance) (3.17.8)
    Requirement already satisfied: beautifulsoup4>=4.11.1 in /opt/conda/lib/python3.12/site-packages (from yfinance) (4.12.3)
    Requirement already satisfied: html5lib>=1.1 in /opt/conda/lib/python3.12/site-packages (from yfinance) (1.1)
    Requirement already satisfied: python-dateutil>=2.8.2 in /opt/conda/lib/python3.12/site-packages (from pandas) (2.9.0.post0)
    Requirement already satisfied: tzdata>=2022.7 in /opt/conda/lib/python3.12/site-packages (from pandas) (2024.2)
    Requirement already satisfied: contourpy>=1.0.1 in /opt/conda/lib/python3.12/site-packages (from matplotlib) (1.3.1)
    Requirement already satisfied: cycler>=0.10 in /opt/conda/lib/python3.12/site-packages (from matplotlib) (0.12.1)
    Requirement already satisfied: fonttools>=4.22.0 in /opt/conda/lib/python3.12/site-packages (from matplotlib) (4.55.3)
    Requirement already satisfied: kiwisolver>=1.3.1 in /opt/conda/lib/python3.12/site-packages (from matplotlib) (1.4.8)
    Requirement already satisfied: packaging>=20.0 in /opt/conda/lib/python3.12/site-packages (from matplotlib) (24.2)
    Requirement already satisfied: pillow>=8 in /opt/conda/lib/python3.12/site-packages (from matplotlib) (11.1.0)
    Requirement already satisfied: pyparsing>=2.3.1 in /opt/conda/lib/python3.12/site-packages (from matplotlib) (3.2.1)
    Requirement already satisfied: soupsieve>1.2 in /opt/conda/lib/python3.12/site-packages (from beautifulsoup4>=4.11.1->yfinance) (2.5)
    Requirement already satisfied: six>=1.9 in /opt/conda/lib/python3.12/site-packages (from html5lib>=1.1->yfinance) (1.17.0)
    Requirement already satisfied: webencodings in /opt/conda/lib/python3.12/site-packages (from html5lib>=1.1->yfinance) (0.5.1)
    Requirement already satisfied: charset_normalizer<4,>=2 in /opt/conda/lib/python3.12/site-packages (from requests>=2.31->yfinance) (3.4.1)
    Requirement already satisfied: idna<4,>=2.5 in /opt/conda/lib/python3.12/site-packages (from requests>=2.31->yfinance) (3.10)
    Requirement already satisfied: urllib3<3,>=1.21.1 in /opt/conda/lib/python3.12/site-packages (from requests>=2.31->yfinance) (2.3.0)
    Requirement already satisfied: certifi>=2017.4.17 in /opt/conda/lib/python3.12/site-packages (from requests>=2.31->yfinance) (2024.12.14)



    
![png](output_60_1.png)
    


<h2>About the Authors:</h2> 

<a href="https://www.linkedin.com/in/joseph-s-50398b136/">Joseph Santarcangelo</a> has a PhD in Electrical Engineering, his research focused on using machine learning, signal processing, and computer vision to determine how videos impact human cognition. Joseph has been working for IBM since he completed his PhD.

Azim Hirjani


## Change Log

| Date (YYYY-MM-DD) | Version | Changed By    | Change Description        |
| ----------------- | ------- | ------------- | ------------------------- |
| 2022-02-28        | 1.2     | Lakshmi Holla | Changed the URL of GameStop |
| 2020-11-10        | 1.1     | Malika Singla | Deleted the Optional part |
| 2020-08-27        | 1.0     | Malika Singla | Added lab to GitLab       |

<hr>

## <h3 align="center"> © IBM Corporation 2020. All rights reserved. <h3/>

<p>

