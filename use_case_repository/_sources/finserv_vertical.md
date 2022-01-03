# Financial Services

In this section we cover data science use cases for the following sub-verticals of financial services:

* [Investment Banking](finsrv.investment.banking)
* [Finance](finsrv.finance)

(finsrv.investment.banking)=
## Investment Banking

<style>
th, td {
padding: 6px;
text-align: left;
vertical-align: top;
font-size: 12px;
}
td.use_case_desc {
	font-size: 10px;
}
th {
  background-color: #666666;
  color: white;
}
tr:nth-child(even) {background-color: #e2e2e2;}
tbody{
    width: 100%;
    display: table;
}
table{
	 width: 100%; 
	 border: 1px solid;
}
</style>

<table>

  <tr>
    <th>Use Cases</th>
    <th>Use Case Sub Group</th>
    <th>Dataset</th>
    <th>Method</th>
    <th>Benefit</th>
    <th>Download Use Case Report</th>
  </tr>

  <tr>
    <td>Investment Portfolio Optimization</td>
    <td>Portfolio Optimization, Robo Advising</td>
    <td>S&amp;P 500 Index data from April1, 2016 to Feb. 1, 2021</td>
    <td>Inverse Optimization and Deep Reinforcement Learning agents, he deep deterministic policy<br>gradient (DDPG) algorithm, Gaussian exploration (OU process)</td>
    <td>Portfolio Rebalancing, Determining the most optimal investment portfolio, including portfolio diversification, based on market data and investor risk preference, less need for investor involvment with high expected ROI, potential increase in customer satisfaction if advisors are able to give them stock recommendations based on a proven prediction algorithm</td>
    <td><a href="./request_use_case_report.html">Request Custom Report</a></td>
  </tr>
  <tr>
    <td>Understanding Multiple Stock Trading Patterns for High ROI</td>
    <td>Stock Price Prediction</td>
    <td>China's CSI800 stock from <a href="http://baostock.com/">baostock.com</a></td>
    <td>Temporal Routing Adaptor (TRA), Optimal Transport (OT)</td>
    <td>Significant gains to investor portfolio, allows investors and advisors to view how different trading strategies can influence ROI over time to make better informed decisions</td>
    <td><a href="./request_use_case_report.html">Request Custom Report</a></td>
  </tr>
  <tr>
    <td>Investment Portfolio Management for Maximizing ROI</td>
    <td>Portfolio Management</td>
    <td>Stock Market Data from January 2, 2002 to March 24, 2020</td>
    <td>Deep Reinforcement Learning, Actor-Critic Reinforcement Learning, Graph Convolutional Networks, Spectral GCN, Autoencoders for feature extraction</td>
    <td>maximize investor's portfolio ROI, identifying market patterns, evaluating trading strategies, and automating workflows</td>
    <td><a href="./request_use_case_report.html">Request Custom Report</a></td>
  </tr>
  <tr>
    <td>Stock Price Predictions</td>
    <td>Stock Price Predictions</td>
    <td>Raw market price data from the Chinese market index (China Securities Index 300 (CSI-300)) with 6 indicators (the closest price, high price, low price, opening price, amount, and volume), China A-share market from January 1, 2010 to December 31, 2019 via Tushare, and open source financial data package.</td>
    <td>Time Series Graph Framework, time series embedding module, visibility graph algorithm for time series transformation, struc2vec, collective influence algorithm, attention-based RNNs, trading simulations to validate profitability and stability of the framework</td>
    <td>obtains the highest average return (47.91%) in trading simulations compared to state-of-the-art baselines, better stock&nbsp;&nbsp;and trade prediction insight, benefits of using a graph-based network for financial time series prediction compared to LSTM, DARNN, DARNN-SA, MFNN, and CA-SFCN</td>
    <td><a href="./request_use_case_report.html">Request Custom Report</a></td>
  </tr>
  <tr>
    <td>Start-up company evaluation and success prediction for investors, data for policy makers related to observable factors, such as diversity in the workplace, that could signal high growth potential</td>
    <td>Start-up Investment Risk</td>
    <td>venture capital dataset from PitchBook covering worldwide VC investment-level activities from 1977 to 2019</td>
    <td>incremental graph learning, graph representation learning, barpartite graphs, Graph Self-aTtention (GST) NN, node-level representation learning, sequential graph representation extraction</td>
    <td>Less risk in start-up investments, Start-up success forecasting, helps to reveal impacts on start-up companies from observable factors such as gender, education, and networking for policy makers</td>
    <td><a href="./request_use_case_report.html">Request Custom Report</a></td>
  </tr>
  <tr>
    <td>Trading strategy for cryptocurrency</td>
    <td>Cryptocurrency Investment Strategy</td>
    <td>Price data from the Binance cryptocurrency exchange API (free) from mid-2017 to April 2021</td>
    <td>k-NearestNeighbor as an example-based learner,&nbsp;&nbsp;eXtreme Gradient Boosting and Random Forest classifiers as tree-based learners</td>
    <td>help investors gain a higher ROI on their crypto investments and which to choose to invest in</td>
    <td><a href="./request_use_case_report.html">Request Custom Report</a></td>
  </tr>
  <tr>
    <td>Stock Market Forecasting and Initial Public Offering (IPO) Planning</td>
    <td>Stock Price Predictions</td>
    <td>S&amp;P500 index data from Yahoo Finance containing highest, lowest, opening, and closing values and the volume of traded stocks for a particular date. </td>
    <td>Regression to predit closing price of stock of a company (Simple Linear, Polynomial, SVR, Decision Tree, and Random Forest), Classification to predict whether the stock will increase or decrease the next day (SVM, KNN, Logistic Regression, Naïve Bayes, Decision Tree, Random Forest)</td>
    <td>potential increase of ROI for investors, early knowledge of next trading day move decisions, a more accurate value and share release predictions based on historical data for IPOs</td>
    <td><a href="./request_use_case_report.html">Request Custom Report</a></td>
  </tr>
  <tr>
    <td>Stock Market Manipulation Detection</td>
    <td>Cryptocurrency Market Manipulation</td>
    <td>Custom dataset of pump and dump schemes carried out on Binance. Trade records: Price, Operation Type (buy/sell), and the UNIX timestamp.</td>
    <td>Random Forest, AdaBoost</td>
    <td>identifying stock market manipulation in crypto and traditional markets, forecasting market manipulation</td>
    <td><a href="./request_use_case_report.html">Request Custom Report</a></td>
  </tr>
  <tr>
    <td>Portfolio Optimization with Predicted ROI</td>
    <td>Portfolio Optimization</td>
    <td>China Securities 100 Index from January 4, 2007 - December 31, 2015</td>
    <td>Random Forest, Support Vector Regression, LSTM, deep multi-layer perceptron (DMLP), CNN</td>
    <td>predicting ROI of investment portfolios, less risk on investments, potential increase of ROI</td>
    <td><a href="./request_use_case_report.html">Request Custom Report</a></td>
  </tr>
  <tr>
    <td>Stock Price Prediction though Social Media Sentimental Analysis</td>
    <td>Stock Price Predictions through Social Media</td>
    <td>Tweets from Twitter API</td>
    <td>Bag of Words (NLP), Random Forest</td>
    <td>finding potential investments, identifying a potential instance of market manipulation, find trending stocks of retail investors or others, stock price prediction</td>
    <td><a href="./request_use_case_report.html">Request Custom Report</a></td>
  </tr>
  <tr>
    <td>Sentimental Analysis of Investors via Social Media App for Investors for Stock Price Forecasting</td>
    <td>Stock Price Predictions through Social Media</td>
    <td>13,771,091 comments/messages from StockTwits (a social media platform for investors) from 2018-2019</td>
    <td>Gradient Boosting Decision Trees (GBDT), LASSO Regression</td>
    <td>distinguishing between experienced investors vs new investors, finding potential investments, understanding sentimental value of a company or stock, potential to predict future market manipulation, potential higher-yield portfolios</td>
    <td><a href="./request_use_case_report.html">Request Custom Report</a></td>
  </tr>
  <tr>
    <td>Day Trading System</td>
    <td>Day/Swing Trading Strategies</td>
    <td>Brazil Stock Exchange: 1824 varying days from January 2, 2015 to December 2019</td>
    <td>Deep Deterministic Policy Gradient (DDPG)</td>
    <td>finding ideal buy/sell times for day and swing traders, predicting stock prices throughout the day, potential for less financial risk for new and experienced day/swing traders</td>
    <td><a href="./request_use_case_report.html">Request Custom Report</a></td>
  </tr>
  <tr>
    <td>Cryptocurrency Price Prediction and Analysis</td>
    <td>Cryptocurrency Stock Price Prediction</td>
    <td>Crypto time series data scraped from Coin Market</td>
    <td>Long Short-Term Memory (LSTM), Mean Absolute Error (MAE)</td>
    <td>Predicting crypto prices, predicting best buy/sell time for the crypto market, Gives businesses an idea of which cryptocurrencies may be beneficial to adopt for future payments</td>
    <td><a href="./request_use_case_report.html">Request Custom Report</a></td>
  </tr>
  <tr>
    <td>Recommendation of High-Return Stocks Based on Correlation Information</td>
    <td>Stock Recommendation</td>
    <td>Chinese stock market: involved 738 stocks, 2223 trading days, and five basic features (i.e., opening<br>price, closing price, highest price, lowest price, and trading volume)</td>
    <td>Stacked Graph Neural Network (GNN), Relation-aware Dynamic Attributed Graph Attention Network (RA-AGAT)</td>
    <td>gives investors a stock selection strategy with the lowest risk and highest return ratio for stocks in China, allows investors outside of China to know which companies would be the best to invest in if they are looking to diversify their portfolio with international stocks</td>
    <td><a href="./request_use_case_report.html">Request Custom Report</a></td>
  </tr>
  <tr>
    <td>Robo-advising for investment portfolio management</td>
    <td>Robo Advising, Portfolio Management</td>
    <td>Customer interraction with robo advisors at a German FinTech institution between February 13-28, 2018</td>
    <td>Partial Least Squares (PLS), Generalized Structured Component Analysis (GSCA)</td>
    <td>More streamlined investing for customers, less overhead for human advisors, can allow human advisors to work with current customers in-depth while robo advisors perform initial onboarding for an overall idea of the customers' needs, potentially less paperwork with having e-documents/agreements for initial portfolio setup</td>
    <td><a href="./request_use_case_report.html">Request Custom Report</a></td>
  </tr>
  <tr>
    <td>Stock Price Fluctuation Over Time based on News Reports</td>
    <td>Stock Price Trends</td>
    <td>Financial Media Data including title, author, source, and release time for 24 listed companies in the same industry from March 10, 2013 to December 30, 2017</td>
    <td>Deep Bidirectional LSTM, Word2Vec (NLP)</td>
    <td>Gives investors a better understanding as to whether the price is increasing due to news alone or because of true company growth, gives investors more insight to make better, more rational investment decisions</td>
    <td><a href="./request_use_case_report.html">Request Custom Report</a></td>
  </tr>

</table>

(finsrv.finance)=
## Finance

<table>

  <tr>
    <th>Use Case</th>
    <th>Use Case Sub Group</th>
    <th>Dataset</th>
    <th>Method</th>
    <th>Benefit</th>
    <th>Download Use Case Report</th>
  </tr>

  <tr>
    <td>Greater protection of financial records and finding weaknesses in current ML models using transaction records</td>
    <td>Increased Data Security</td>
    <td>Client transaction records listing type of transaction, transaction amount, and a timestamp for each transaction from three different financial institutions</td>
    <td>Adversarial Attack and Defense using NLP Models: Masked Language Model (MLM), Fast Gradient Sign Method (FGSM), Concat FGSM, LM FGSM, Concat Sampling Fool (Concat SF), Sequential Concat Sampling Fool (Seq Concat SF)</td>
    <td>improved fraud detection and scoring system by banks, potential for more secure system to protect data</td>
    <td><a href="./request_use_case_report.html">Request Custom Report</a></td>
  </tr>
  <tr>
    <td>Differential Privacy </td>
    <td>Increased Data Privacy/Security</td>
    <td>Lending Club dataset from 2016-2017</td>
    <td>Logistic Regression and Gradient Boosting Trees for Diffrerential Privacy (DP), and Random Forest for predict the credit conversion factor (CCF), beta regression, linear regression</td>
    <td>increased privacy while retrieving information, specifically for credit risk</td>
    <td><a href="./request_use_case_report.html">Request Custom Report</a></td>
  </tr>
  <tr>
    <td>Attracting New Customers and Customer Retention</td>
    <td>New Customers and Customer Retention</td>
    <td>Kaggle and UC Irvine Machine Learning Repo relating to banking (accounts, loans, transactions, mobile banking, engagement, and credit accounts) and general information about an individual (demographic, occupation, health, wealth &amp; assets, social activities)</td>
    <td>Multi-Task Learning, dynamic feature selection, Logistic Regression</td>
    <td>creating new, attractive products based on dynamic feature selection, increase of transactions for financial institution</td>
    <td><a href="./request_use_case_report.html">Request Custom Report</a></td>
  </tr>
  <tr>
    <td>Credit Score Assessment and Default Probability</td>
    <td>Probability of Default Based on Credit Score</td>
    <td>Lending company data from the Polish Credit Bureau</td>
    <td>Logistic Regression, Logistic Regression with weight evidence (WOE) transformations, Random Forest, Gradient Boosting Models (GBM), and Extreme Gradient Boosting Model (XGB)</td>
    <td>Automatically assessing credit risk and potential for default</td>
    <td><a href="./request_use_case_report.html">Request Custom Report</a></td>
  </tr>
  <tr>
    <td>Financial Crime and Money Laundering Detection and Prevention</td>
    <td>Fraud Detection and Prevention</td>
    <td>Bank data including: Transaction ID, Account ID, Account/Customer Type, Product/Transaction Type, Transaction Code, Transaction Branch, Source Bank, Destination Bank, Transaction Amount, Average Amount of Transactions in Previous Month, Transaction Currency, Credit/Debt Status, Country of Origin, Country of Destination, Credit Score</td>
    <td>Classification, Anomaly Detection, Logical AND on results, Snorkel model</td>
    <td>proposed model aimed to detect fraud with minimal human intervention, larger-scale automatic fraud detection at financial institutions, decrease potential money laundering crimes at financial institutions</td>
    <td><a href="./request_use_case_report.html">Request Custom Report</a></td>
  </tr>
  <tr>
    <td>Customer Churn Prediction in Banking Industry</td>
    <td>Customer Churn Prediction</td>
    <td>Public dataset from Kaggle containing 28,382 records and 21 features (attributes) of demographic information, customer bank relationship, and transactional informaino such as current balance. </td>
    <td>Data Pre-processing: Exploratory Data Analysis and Bivariate Analysis , ML Models: Logistic Regression, Decision Tree, K Nearest Neighbor, Random Forest</td>
    <td>customer retention, customer churn prediction</td>
    <td><a href="./request_use_case_report.html">Request Custom Report</a></td>
  </tr>
  <tr>
    <td>Credit Rating Prediction and Risk Assessment</td>
    <td>Risk Assessment based on Credit Rating</td>
    <td>Financial Ratings: a time-series dataset of income from about 302 companies from MCM (Contemporary Undergraduate Mathematical Contest in Modeling - <a href="http://en.mcm.edu.cn/">http://en.mcm.edu.cn</a>)</td>
    <td>Lasso and recursive feature elimination to find key features. Random Forest, SVM, and Gradient Boosted Classification.</td>
    <td>Assessing credit risks for individuals and companies, insight to create new policies, minimize financial loss and risk for financial institutions</td>
    <td><a href="./request_use_case_report.html">Request Custom Report</a></td>
  </tr>
  <tr>
    <td>Counterfeit Currency Detection </td>
    <td>Fraud Detection and Prevention</td>
    <td>UC Irvine Machine Learning Repository: images of real and forged currency. 1372 total instances and 5 attributes</td>
    <td>SVM, Random Forest, Logistic Regression, Naïve Bayyes, Decision Tree, K-Nearest Neighbor</td>
    <td>currency fraud detection, decrease potential of crime related to counterfeit money, potentially less human error when checking for real vs fake currency</td>
    <td><a href="./request_use_case_report.html">Request Custom Report</a></td>
  </tr>
  <tr>
    <td>Risk Prediction for Bank Loan Approvals</td>
    <td>Bank Loan Risk Assessment</td>
    <td>Kaggle Competition Dataset. Loan applicants featuring 13 attributes: loan ID, gender, marriage status, dependents, education, self employment, income, co-applicant income, loan amount, loan amount term, credit history, property area, and loan status</td>
    <td>Logistic Regression, Random Forest</td>
    <td>less finanical risks for banks pertaining to loans, automated approval/denial for loan applications, faster approval/denial process</td>
    <td><a href="./request_use_case_report.html">Request Custom Report</a></td>
  </tr>
  <tr>
    <td>Marketing and Sales in Busineses and Bank</td>
    <td>New Customers and Customer Retention</td>
    <td>UC Irvine Machine Learning Repository: direct marketing campaigns of a Portuguese banking institution. It consists of 45k instances with 16<br>different attributes (age, job, marital, education, default,<br>balance, housing, loan, contact, day, month, duration,<br>campaign, pdays, previous, poutcome, and the outcome).</td>
    <td>Decision Tree, K-Nearest Neighbor, Random Forest, Naïve Bayes, Support Vector Machine</td>
    <td>Sales Forecasting, Predicting Customer Preferences, Business and Customer Growth, Enhance Sales Agent Performance</td>
    <td><a href="./request_use_case_report.html">Request Custom Report</a></td>
  </tr>
  <tr>
    <td>Credit Risk Prediction and Probability of Customer Default</td>
    <td>Credit Risk and Loan Defaulting</td>
    <td>Dataset 1: customer demographics, credit history, loan amount, loan duration, etc. , Dataset 2: customer demographics, history of payment, credit data, payments and bill statements of credit card clients residing in Taiwan from April 2005 to September 2005</td>
    <td>Feature Extraction: Principal Component Analysis (PCA) and Linear Discriminant Analysis (LDA), ML: Multiple Linear Regression, Logistic Regression, SVM, KNN, Kernel SVM, Decision Tree, Random Forest, Naïve Bayes, and Gaussian Naïve Bayes</td>
    <td>Allows financial institutions to invest in safer options, less risk of losing money to customers who default on their loan, potential for a more stable financial balance throughout the years, more efficient approval/denial process based on output, reducing capital loss</td>
    <td><a href="./request_use_case_report.html">Request Custom Report</a></td>
  </tr>
  <tr>
    <td>Predicting Loan Defaulters</td>
    <td>Loan Defaulting</td>
    <td>Realtime data from Kaggle which illustrates loan administration <br>experience within the U.S. small business social circle </td>
    <td>Principal Component Analysis (PCA), Linear Discriminant Analysis (LDA), Logistic Regression with Stochastic Gradient Descent (SGD), Random Forest, K-Nearest Neighbor (KNN)</td>
    <td>balanced or gain in capital, more efficient loan approval proccess, more efficient lending process without guessing about customer's potential to default and the bank to lose money, less risk to the employee or company when lending money to customers</td>
    <td><a href="./request_use_case_report.html">Request Custom Report</a></td>
  </tr>
  <tr>
    <td>Credit Risk Assessment for Supply Chain Finance</td>
    <td>Credit Risk Assesment</td>
    <td>Small and Mid-sized Enterprise data from the Computer and Electronic Communications Manufacturing Industry</td>
    <td>Firefly Algorithm Support Vector Machine (FA-SVM)</td>
    <td>analyzing the credit risk of supply chain companies rather than individuals, less risk of financial loss when giving out business loans, understanding which companies the bank can trust to increase or decrease loan credit to mitigate a loss</td>
    <td><a href="./request_use_case_report.html">Request Custom Report</a></td>
  </tr>
  <tr>
    <td>Indentifying Fraudulent Financial Statements</td>
    <td>Financial Crime Prevention</td>
    <td>Fraud Financial Statements from Chinese publically traded companies from 2006-2019</td>
    <td>Pearson Correlation Coefficient, Naïve Bayes (Kernel), SVM, KNN, Decision Trees, Logistic Regression</td>
    <td>capital gain if with the reduction of fraud cases, early fraud detection to mitigate loss, less risk in lending</td>
    <td><a href="./request_use_case_report.html">Request Custom Report</a></td>
  </tr>
  <tr>
    <td>Implementing Blockchain Technology in the Banking Sector</td>
    <td>Blockchain in Banking</td>
    <td>Blockchain consultants, Blockchain marketing experts, CEOs/business heads that are in the process of advising, consulting, or implementing blockchain technology</td>
    <td>Confirmatory Factor Analysis (CFA), Principal Component Analysis (PCA), </td>
    <td>increased privacy and security to company and customer data, potentially higher customer trust due to more complex security measures, improve transparancy and tracability of transactions, streamline business process, save money overall through a more secure and efficient banking and security process, reduce fraud, reduced human intervention</td>
    <td><a href="./request_use_case_report.html">Request Custom Report</a></td>
  </tr>
  <tr>
    <td>Creating an More Efficient ATM Service Model</td>
    <td>ATM Services</td>
    <td>Transactions in ruble ATMs with a cash recycling function<br>containing records of cash deposits and withdrawals, as well as on collections from February to September 2018</td>
    <td>Linear Regression, Lasso, Ridge Regression, Elastic Network, Gradient Decision Trees, Random Forests, and SVMs</td>
    <td>increase efficient cashflow management in ATMs, helps to ensure the right amount of cash is available in the ATM without risking a loss if the ATM malfunctions or the excess money is taken out somehow, reduces cost for financial monitoring, predicting supply and demand of ATM and overall company cashflow from bank to customer and customer to bank</td>
    <td><a href="./request_use_case_report.html">Request Custom Report</a></td>
  </tr>
  <tr>
    <td>Detecting Fraudulent Credit Card Transactions</td>
    <td>Fraud Detection and Prevention</td>
    <td>Customer credit card transaction data from ULB Machine Learning Group downloaded from Kaggle</td>
    <td>Autoencoders, Multi-Layer Perceptron, KNN, Logistic Regression</td>
    <td>minimize losses from fraudulent transations for credit card issuing banks, more accurate fraud detection, improve customer trust with better fraud detection</td>
    <td><a href="./request_use_case_report.html">Request Custom Report</a></td>
  </tr>
  <tr>
    <td>Credit Score Evaluation</td>
    <td>Credit Risk Assesment</td>
    <td>Customer credit data</td>
    <td>Naïve Bayes, Logistic Regression, Random Forest, Decision Tree, KNN</td>
    <td>lower risk in P2P lending, less human intervention, less overhead costs due to a more automated process</td>
    <td><a href="./request_use_case_report.html">Request Custom Report</a></td>
  </tr>
  <tr>
    <td>Bank Customer Classification to Provide Advice for Banks to Better Manage Customer Relationships</td>
    <td>Bank/Customer Relationship</td>
    <td>Customer data consisting of customer ID, age, and credit score</td>
    <td>Multi-Class Extreme Learning Machine (ELM), Label Proportions (LLP)</td>
    <td>Building better relationships with customers, customer retention and higher reviews, more referals, brand/customer loyalty, lower customer churn rate</td>
    <td><a href="./request_use_case_report.html">Request Custom Report</a></td>
  </tr>

</table>
