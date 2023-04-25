# Python_stock_price_data_analysis_sample_pandas_ta


Pythonでできる！ 株価データ分析
https://www.morikita.co.jp/books/mid/085711

- 2023/04 より Google Colaboratory で Ta-Libが動かなくなったため pandas_ta で再作成


サンプルコード一式

![085711cvr](https://user-images.githubusercontent.com/6063541/213907253-a3718b4d-8a66-49e4-84a2-650789dd73a3.jpg)

- サンプルコード変更点

|<br>|TA-LIb|pandas_ta|
|--|--|--|
|import文	| import talib as ta	| import pandas_ta as ta |
|移動平均	| df['ma5'] = ta.SMA(close ,timeperiod=5)<br>df['ma25'] = ta.SMA(close ,timeperiod=25	| df['ma5'] = ta.sma(close ,length=5)<br>df['ma25'] = ta.sma(close ,length=25) |
|ボリンジャー<br>バンド | df['upper1'], df['middle'], df['lower1'] = ta.BBANDS(close, <br> 　timeperiod=25, nbdevup=1, nbdevdn=1, matype=0)<br><br>df['upper2'], df['middle'], df['lower2'] = ta.BBANDS(close, <br>　　timeperiod=25, nbdevup=2, nbdevdn=2, matype=0)| bb1 = ta.bbands(close, length=25, std=1.0, mamode="sma")<br>bb2 = ta.bbands(close, length=25, std=2.0, mamode="sma")<br><br>df["upper1"], df["lower1"] = bb1["BBU_25_1.0"], bb1["BBL_25_1.0"]<br>df["upper2"], df["lower2"] = bb2["BBU_25_2.0"], bb2["BBL_25_2.0"] |
|RSI | rsi14 = ta.RSI(close, timeperiod=14)<br>rsi28 = ta.RSI(close, timeperiod=28)| rsi14 = ta.rsi(close, length=14)<br>rsi28 = ta.rsi(close, length=28)|
|MACD | macd, macdsignal, hist = ta.MACD(close, fastperiod=12, slowperiod=26, signalperiod=9)<br>df['macd'] = macd<br>df['macd_signal'] = macdsignal<br>df['hist'] = hist| mdf = ta.macd(close, fast=12, slow=26, signal=9)<br>df['macd'] = mdf['MACD_12_26_9']<br>df['macd_signal'] = mdf['MACDs_12_26_9']<br>df['hist'] = mdf['MACDh_12_26_9']|
|ストキャスティクス | slowK, slowD = ta.STOCH(df["High"], df["Low"], close,<br>         fastk_period=5, slowk_period=3,<br>          slowk_matype=0, slowd_period=3, <br>         slowd_matype=0)<br>df['slowK'], df['slowD'] = slowK, slowD| sdf = ta.stoch(df["High"], df["Low"], close, k=5, d=3, smooth_k=3, mamode="sma")<br>df['slowK'], df['slowD'] = sdf['STOCHk_5_3_3'], sdf['STOCHd_5_3_3']|
