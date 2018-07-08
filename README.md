﻿
# About this project

MyShogi is an open source GUI for computer Shogi engine.

MyShogiは、オープンソースの将棋ソフト用GUIです。
2018年にマイナビ出版さんから発売する商用版のやねうら王用のGUIとして開発が始まりました。

# スクリーンショット

- やねうら王の公式Twitterの画像をそのまま貼り付けたため、縦横の比率がおかしいです。

|||
|---|---|
|<img src="https://pbs.twimg.com/media/Dez3gZxVAAASWWY.jpg" width="400" height="254" alt="対局設定">|<img src="https://pbs.twimg.com/media/Dg6DMjYUcAAol41.jpg" width="400" height="254" alt="盤面編集">|
|<img src="https://pbs.twimg.com/media/DhP9uLkUEAAue8I.jpg" width="400" height="254" alt="対局画面">|<img src="https://pbs.twimg.com/media/Dez3hKnUcAANNd9.jpg" width="400" height="254" alt="成り不成">|
|<img src="https://pbs.twimg.com/media/DhmEiQ-UYAATJQF.jpg" width="400" height="254" alt="エンジン選択">|<img src="https://pbs.twimg.com/media/Dem5sS2U0AEjgC7.jpg" width="400" height="254" alt="利きマーカー">|
<img src="https://pbs.twimg.com/media/Deb12RyV0AA7ZCw.jpg" width="400" height="254" alt="英字駒">|<img src="https://pbs.twimg.com/media/Deb13B4VMAAYAfZ.jpg" width="400" height="254" alt="1文字駒">|


# 特徴

- オープンソース
- エンジン設定などがユーザーフレンドリー
- 思考エンジン開発者のデバッグに役立つような優しい作り
- コアな部分は、pure C#で書かれている。(ほぼフルスクラッチ)
- View以外は実行環境への依存低めに書いてあるので移植性に優れている
- Viewも環境依存、かなり低め。(対局画面はBitmapの矩形転送と文字描画のみ)
- Headlessモード(GUIなしモード)搭載で、pythonなどから呼び出して対局させることが出来る
- レスポンシブな画面デザイン(ウィンドウサイズ可変、幅を狭めると縦長の駒台になるなど)

…になる予定

# 実装済みの機能、細かな特徴など

- たくさんあって書ききれないのでこちらをどうぞ。→　[実装済みの機能](MyShogi/docs/実装済みの機能.md)

# 初回リリースで実装する予定の機能

- わかりやすいエンジン設定
- コンピューターの段位選択機能
- CPU自動判定
- 通常対局機能(駒落ち対局含む)
- 詰将棋エンジンの利用
- 検討機能
- 盤面編集機能
- PV(読み筋)の可視化
- 形勢のグラフ表示
- KIF/KI2/CSA/SFEN/PSN/[PSN2](MyShogi/docs/PSN2format.md)/JSON/JKF/LiveJSON形式の棋譜の入出力機能。分岐棋譜対応。
- 入玉宣言勝ちの条件変更(24点法、27点法、トライルール)

# 商用版について

## 商用版にのみ搭載される機能

- 各思考エンジンのエンジンバナー
- 指し手の読み上げ(音声)、秒読み(音声)
- インターネット非公開の評価関数ファイル(どのソフトかは考え中)
- やねうら王の非公開定跡ファイル

## 商用版『やねうら王 2018』に搭載される予定のエンジン

- tanuki-(2018年版) : WCSC28版からR50ぐらいup
- tanuki-(SDT5 優勝バージョン)
- Qhapaq(2018年版)
- 読み太(2018年版)
- やねうら王(2018年版) : KPP_KKPT型 , depth 12の教師50億局面から学習

## 商用版に関する記事

- 商用版について詳しいことは、こちらの記事をどうぞ。→ [PC将棋ソフト「将棋神 やねうら王」に関してお答えします](http://yaneuraou.yaneu.com/2018/06/15/pc%E5%B0%86%E6%A3%8B%E3%82%BD%E3%83%95%E3%83%88%E3%80%8C%E5%B0%86%E6%A3%8B%E7%A5%9E-%E3%82%84%E3%81%AD%E3%81%86%E3%82%89%E7%8E%8B%E3%80%8D%E3%81%AB%E9%96%A2%E3%81%97%E3%81%A6%E3%81%8A%E7%AD%94/)

- 要望については、こちらの記事のコメントにどうぞ。→　[将棋ソフト用GUI MyShogi、要望受付中](http://yaneuraou.yaneu.com/2018/05/31/%E5%B0%86%E6%A3%8B%E3%82%BD%E3%83%95%E3%83%88%E7%94%A8gui-myshogi%E3%80%81%E8%A6%81%E6%9C%9B%E5%8F%97%E4%BB%98%E4%B8%AD/)

# 将来的に実装するかも知れない機能

※　案を書いているだけで、対応を約束するものではありません。また、一部機能は商用版のみに搭載するかも知れません。予め、ご了承ください。

// 実装予定
- 局面図の画像出力機能
- 2盤面同時表示、4盤面同時表示、8盤面同時表示、etc…
- 多面指し機能

// 対応を検討中

- 将棋所、ShogiGUIにある機能はだいたい実装していく予定です。

- 対局
	- 中断局の再開処理(中断するまでの最後の指し手の時間が加算されてその時の持ち時間のまま対局を再開出来るように)
	- 持ち時間が減る時の画面描画、最小矩形にして高速化する
	- 戦型判定～囲い完成時のエフェクト等
	- コンピュータの指す戦型を指定するモード(GUIだけでは限界があるような…)
	- 手加減モード , 接待モード等 , 指導対局
	- MultiPonder(ponderを複数のインスタンスに対して同時に行う)
	- クラスター探索機能

- 検討機能
	- 検討機能に悪手率の計測等
	- (人間の)棋力判定機能
	- 局面の自動抽出機能(検討モードで特定の条件に合致する局面図をファイルに書き出す)
	- 即席詰将棋機能、中盤終盤課題局面生成機能、評価値当てクイズetc…
	- 感想戦機能(日本語文書での棋譜の自動解説)
	- 棋戦の観戦機能
	- 局面の激しさ(思考を深めて行ったときの指し手の安定度等を)を何らか可視化
- 思考の可視化
	- 評価値グラフの縦軸をlogや期待勝率で表示する機能

- 鑑賞用
	- 白地に黒文字の漢字1文字駒(局面図の出力用に)

- 定跡
	- 定跡編集機能
	- 定跡自動生成機能
	- 駒落ち定跡

- タブレット端末向け
	- 後手の駒の成り・不成のダイアログ、駒、キャンセルの文字を180度回して表示する機能。
	- 駒台を上下に表示する超縦長のモードがあってもいいのでは。

- 自己対局
	- 蠱毒(複数のソフトの自動対局、自動レーティング算出)
	- 並列自動対局(ソフトの自己対局を複数インスタンスで同時に行う)
	- 指定局面(フォルダのなかのKIFファイルすべてを対象とする)からの連続自動対局

- SNS対応
	- エンジンによる検討内容をツイート機能
	- スクリーンショットの撮影など

- 通信対局
	- 通信対局(1対1)
	- floodgate対応
	- AWSにエンジンを配置しての利用
	- オンライン対局

- 国際化
	- 多言語対応

- 移植
	- Mac/Linux対応。ニーズ、作業量を検討した上で。
	- スマホ版(iOS/Android)
	- ブラウザ版 , ブラウザ版によるオンライン対局

- 他ルール
	- 王手将棋
	- ついたて将棋等

- その他
	- メニューの下にあるボタン(toolstrip)のカスタマイズ機能
	- 音声認識対応(目隠し将棋が捗る)

- 開発用
	- ベンチマーク
	- Headlessモード(GUIなしモード)搭載。pythonなどから呼び出して対局させられるように。
	- 教師局面のクラスターを用いた生成
	- [USI2.0](MyShogi/docs/USI2.0.md)対応


# 本GUIが対応する思考エンジン

USIプロトコル対応のエンジンならば問題なく使えます。
[USI2.0](MyShogi/docs/USI2.0.md)をサポートしているのがベストなので、一番のお勧めは、やねうら王です。その次にお勧めなのは、やねうら王系のエンジンです。

- [やねうら王](https://github.com/yaneurao/YaneuraOu)
- [tanuki-](https://github.com/nodchip/tnk-)
- [読み太](https://github.com/TukamotoRyuzo/Yomita)

# 使い方

USIプロトコル対応の将棋エンジンが使えます。

// 以下、書きかけ

# 本プロジェクトが提案するフォーマット

- [PSN2format](MyShogi/docs/PSN2format.md) : PSN形式から改良された棋譜ファイルフォーマット
- [USI2.0](MyShogi/docs/USI2.0.md) : USIプロトコルから改良されたプロトコル

# 謝辞

本GUIを使ってくださる皆様、開発に関わってくださった皆様、誠にありがとうございます。

- tanuki-のエンジン開発者の野田さん、那須さん、たぬきチームのメンバー
- Qhapaqの澤田さん、読み太の塚本さん
- WhaleWatcherのソースコードを提供してくれた、えびふらいさん
- GUIの開発を協力してくれたMizarさん
- レーティング計測にご協力いただいたuuunuuunさん
- やねうら王に貢献してくださっている方々
- Stockfishの開発チーム

# ライセンス

- ソースコードはGPLv3
- ただし画面素材、音声素材の単体配布(二次利用等)は禁止(マイナビ出版に権利があるため)
