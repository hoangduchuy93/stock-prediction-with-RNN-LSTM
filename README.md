![image](https://user-images.githubusercontent.com/91864024/181411108-e8dde772-30c5-4e84-83cf-7d00485229c8.png)
# Stock Prediction With RNN LSTM
## I. Outline
- Stock price prediction is one of the methods that investors can refer to to choose the best time to buy/ sell stocks.
- Predicting the opening price (Open) is one of the important criteria to determine the desired value in buying/selling stocks.
- Open price prediction model (Open) based on other parameters such as previous opening price, closing price, volume, ... using RNN LSTM to make a suggested forecast for investors
## II. Business Objective/ Problem
- Assume that you work in the Data Science department of a securities company. Your task is to make a prediction on the opening price of the stock so that the broker can make recommendations for investors.
- The securities company you are working with wants to have a model that helps them predict the movement of stocks, thereby making recommendations to customers at the right time to buy/sell stocks.
- In this project, we will forecast the opening price (Open) based on one or more parameters such as previous opening price, closing price, volume, ...
## III. Project implementation
### 1. Business Understanding
Based on the above description => identify the problem:
- Find methods to predict stock prices to recommend to investors.
- Objectives/problems: build a prediction model can work with data collected from securities database and make the model to recommend to investors.
- Applied mothods:
  - Option 1: predict the tomorrow's Open value based on the today's Open value.
  - Option 2: predict the tomorrow's Open value based on the today's Open, High, Low, Close, Adj Close, Volume
  - Model suggestion: RNN LSTM. Find better options among these 2 for prediction model.
### 2. Data Understanding/ Acquire
- Use AAPL.csv dataset or dowload from link https://finance.yahoo.com/quote/AAPL/history?period1=1479081600&period2=1605312000&interval=1d&filter=history&frequency=1d&includeAdjustedClose=true
- This dataset includes 1008 rows and 7 feature variables:
  - Date: time the stock is recorded. The duration is from 2016-11-14 to 2020-11-13
  - Open: price at the opening session
  - High: the highest price of the day
  - Low: the lowest price of the day
  - Close: the closing price of the day
  - Adj close: price at which the last lot of the stock is bought or sold in the last trading session
  - Volume: number of shares traded during the session

![image](https://user-images.githubusercontent.com/91864024/181418746-7318681e-30b3-451c-bb57-8b4ee90c2444.png)

### 3. Build model
#### 3.1. Understand the dataset:
![image](https://user-images.githubusercontent.com/91864024/181419374-41ed41df-0555-4136-9ab5-238f785a8f4c.png)

#### 3.2. Preprocessing
**- Check NaN, Null, remove duplicate**

![image](https://user-images.githubusercontent.com/91864024/181420746-e1726ab1-dd29-4df4-ae0d-fe178f88c5d7.png)

**- Normalization**

![image](https://user-images.githubusercontent.com/91864024/181420847-eed51399-ab1a-4550-ae2c-791635bb9921.png)

**- Split into train and test sets**

![image](https://user-images.githubusercontent.com/91864024/181422430-6ec0815c-52a4-4142-ace7-5f6d503df0eb.png)
















