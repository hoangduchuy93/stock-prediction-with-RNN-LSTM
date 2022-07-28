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

###A. Predict the tomorrow's Open value based on the today's Open value.

![image](https://user-images.githubusercontent.com/91864024/181432716-2b4ed44d-1765-4c85-b716-e39e1819237d.png)

**- RNN LSTM model**

![image](https://user-images.githubusercontent.com/91864024/181432938-4ed4d5b4-b154-4946-b126-bd2c6cab2c1b.png)
![image](https://user-images.githubusercontent.com/91864024/181433266-b2796790-2f41-4740-aa3a-1037b1b2890b.png)
![image](https://user-images.githubusercontent.com/91864024/181433043-03544ac1-61b8-4db7-9f44-b2c6c178c82c.png)

Comment: after 50 iterations the loss of train and test was almost equal.

**- Prediction**

![image](https://user-images.githubusercontent.com/91864024/181433636-cd064899-32c6-418e-8632-c35077b8e233.png)
![image](https://user-images.githubusercontent.com/91864024/181433693-fa76ba74-4a9e-41b0-8ee5-52fa6b40c4cd.png)

Comment: mean(Open) ~ 55, test MAE ~ 7.18 --> model can predict with difference from mean of 7.18/ 55 ~ 13%, can be used for prediction

![image](https://user-images.githubusercontent.com/91864024/181433933-b05091b2-7fc9-416e-a823-68d080106c0d.png)

Comment: the training line is quite close to the real data, the test line compared to the real data is slightly different but not overfitting, acceptable with a difference of 13% from the mean.

### B. Predict the tomorrow's Open value based on the today's Open, High, Low, Close, Adj Close, Volume
![image](https://user-images.githubusercontent.com/91864024/181434928-e66936d2-3c7e-4273-8a4d-425fcdf784d4.png)

![image](https://user-images.githubusercontent.com/91864024/181435336-58ebfcf8-d9c4-45ef-950b-f591f1e2fcdf.png)

Comment: the Open, High, Low, Close, Adj Close columns have the same shape, they all increase over time. The Volume column has spikes that coincide with the peaks of the remaining columns (trading volume increases sharply -> closing prices, highs, lows, corrections also spike at the peaks)

**- RNN LSTM model**

![image](https://user-images.githubusercontent.com/91864024/181436298-e7fe5471-caa6-44cf-9b70-1d0d70af882b.png)

![image](https://user-images.githubusercontent.com/91864024/181436383-766ca42d-5cc3-4163-bf8c-552f50a76974.png)

Comment: at 50 iterations, the loss of train and test is almost the same

**- Prediction**

![image](https://user-images.githubusercontent.com/91864024/181436925-275dd75a-0b4d-4fc7-9529-7c54e40a691f.png)

Comment: mean of Open ~ 55, MAE of test ~ 1.2 --> model can predict Open with difference from mean is 1.2/55 ~ 2.2% --> model can be used well in prediction

![image](https://user-images.githubusercontent.com/91864024/181437064-6d1b4ba9-c143-4009-8a99-636441ec69da.png)

Comment: there is difference between real and predict in some positions

![image](https://user-images.githubusercontent.com/91864024/181437325-2eca0053-7768-42f7-8aa2-24fa61be498a.png)

Comment: the test closely follows the real data. However, in some peaks / troughs, the prediction model is not completely accurate, but most of them match -> the model is suitable for predicting Open

![image](https://user-images.githubusercontent.com/91864024/181439455-4841d183-0b71-4866-a782-7e94b1d7f936.png)

### 4. Conclusion

- Based on the above analysis, 2 models are suitable to use in Open prediction.
- Compared with using 1 input (Open) to predict Open, the model using all columns to predict Open gives better results (one-to-one: MAE/mean ~ 13%, many-to-one: MAE/means ~ 2%)

Thank you for your experience with my project. Hope you enjoy it!


