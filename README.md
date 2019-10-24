# 日本語プログラミング言語「プロデル」で機械学習と自然言語処理をするためのコード群

## ナイーブベイズ

## サポートベクタマシン

### 使い方
0. `サポートベクタマシン.rdr`を参照します。
0. 何らかのカーネル関数となる種類のインスタンスを作ります。今のところ，線形カーネルが実装されています。
0. サポートベクタマシン種類のインスタンスを作ります。この際に，先に作ったカーネル関数のインスタンスを引数に設定します。
0. `［サポートベクタマシン種類のインスタンス］が【訓練用データ】と【正解ラベル】を【｛閾値，学習率｝】で学習する`を実行して学習します。
0. `［サポートベクタマシン種類のインスタンス］が【推定したいデータ】を推定する`を実行して推定します。

### 種類と手順

#### サポートベクタマシン種類

##### 手順

###### コンストラクタ
* 引数：カーネル関数のインスタンス
* 戻り値：なし

###### 自分が【データ：行列】と【正解：行列】を【引数：配列】で学習する手順
サポートベクタマシンを訓練します。最急降下法を使って，パラメータを探索します。
* 引数（と）：訓練データです。行列型です。1つのデータが1行に対応します。例えば，784次元のデータが60000個ある場合は，60000行784列の行列を作ります。
* 引数（を）：正解ラベルです。行列型です。1つのラベルが1行に対応します。ラベルは，1または-1の値を取ります。データが60000個ある場合は，60000行1列の行列を作ります。
* 引数（で）：閾値と学習率をこの順で配列型にしてください。最急降下法の勾配が閾値以下になるとイテレーションを終了します。学習率×勾配の値がパラメータの更新に使われます。大きすぎると勾配が振動・発散します。
* 戻り値：なし

##### 自分が【データ：行列】を推定する手順
訓練したサポートベクタマシンを使ってデータからラベルを推定します。
* 引数（を）：データです。行列型です。1つのデータが1行に対応します。例えば，784次元のデータが10000個ある場合は，10000行784列の行列を作ります。
* 戻り値：推定したラベルが行列型で返されます。縦ベクトルです。データが10000個ある場合は，10000行1列の行列が返ります。

##### パラメータ
サポートベクタマシンの訓練時に計算されたパラメータにアクセスできます。行列型で，1行につき1つのデータが対応します。これはラグランジュ未定乗数法の係数です。

#### 線形カーネル種類

##### コンストラクタ
* 引数：訓練用のデータです。行列型です。
* 戻り値：なし

##### 自分で【推定用データ：行列】を計算する手順
* 引数（を）：データです。行列型です。
* 戻り値：カーネル関数の計算結果を返します。行列型です。

##### 全部
訓練時に使用するカーネル関数の計算結果です。


## 条件付き確率場

## ニューラルネットワーク

1行が1つのデータに対応します。10次元のデータを100個ならべたミニバッチは，100行10列の行列で表されます。テンソルには対応しません。

### 種類と手順

#### 全結合層種類

##### コンストラクタ
* 引数：隠れ層のパラメータとバイアスをこの順で指定します。いずれも行列型です。バイアスは横ベクトル（1行N列の行列）です。
* 戻り値：なし

##### 自分が【X：行列】を順伝播させる手順
* 引数（を）：入力となるデータを行列型で指定します。
* 戻り値：XW+Bを返します。行列型です。

##### 自分が【入力：行列】を逆伝播させる手順
* 引数（を）：出力層側から来るデータを指定します。行列型です。
* 戻り値：微分の結果を返します。行列型です。

##### 行列dW

##### 行列dB

#### ソフトマックスに損失関数もくっつけたやつ種類

##### コンストラクタ
何もしません

##### 自分が【X：行列】を【T:行列】で順伝播させる手順
* 引数（を）：入力となるデータを行列型で指定します。
* 引数（で）：正解ラベルです。正解ラベルは，one-hotベクトルでなければなりません。1つのデータにつき1行が対応します。100個のデータがある場合は，100行の行列です。
* 戻り値：損失関数の値が1行1列の行列型で返されます。

##### 【自分】が逆伝播させる手順
* 戻り値：微分の結果を返します。行列型です。

#### ランプ関数種類
いわゆるReLUです。

##### 自分が【X：行列】を順伝播させる手順
* 引数（を）：入力となるデータを行列型で指定します。
* 戻り値：ReLUの計算結果を返します。行列型です。

##### 自分が【入力：行列】を逆伝播させる手順
* 引数（を）：出力層側から来るデータを指定します。行列型です。
* 戻り値：微分の結果を返します。行列型です。

## 単語分散表現

## 系列ラベリング

## テキスト分類
