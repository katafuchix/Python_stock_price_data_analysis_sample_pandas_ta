# Python_stock_price_data_analysis_sample_pandas_ta


Pythonでできる！ 株価データ分析
https://www.morikita.co.jp/books/mid/085711

- 2023/04 より Google Colaboratory で Ta-Libが動かなくなったため pandas_ta で再作成
- 8.2 　ローソク足パターン　以外 動作確認済み

サンプルコード一式

![085711cvr](https://user-images.githubusercontent.com/6063541/213907253-a3718b4d-8a66-49e4-84a2-650789dd73a3.jpg)

|<br>|TA-LIb|pandas_ta|
|--|--|--|
|import文	| import talib as ta	| import pandas_ta as ta |
|移動平均	| df['ma5'] = ta.SMA(close ,timeperiod=5)<br>df['ma25'] = ta.SMA(close ,timeperiod=25	| df['ma5'] = ta.sma(close ,length=5)<br>df['ma25'] = ta.sma(close ,length=25) |
|ボリンジャーバンド | df['upper1'], df['middle'], df['lower1'] = ta.BBANDS(close, <br> 　timeperiod=25, nbdevup=1, nbdevdn=1, matype=0)<br><br>df['upper2'], df['middle'], df['lower2'] = ta.BBANDS(close, <br>　　timeperiod=25, nbdevup=2, nbdevdn=2, matype=0)| bb1 = ta.bbands(close, length=25, std=1.0, mamode="sma")<br>bb2 = ta.bbands(close, length=25, std=2.0, mamode="sma")<br><br>df["upper1"], df["lower1"] = bb1["BBU_25_1.0"], bb1["BBL_25_1.0"]<br>df["upper2"], df["lower2"] = bb2["BBU_25_2.0"], bb2["BBL_25_2.0"] |
