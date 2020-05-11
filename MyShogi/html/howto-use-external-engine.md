<style>
img {
    width: 80%;
    margin-left: 10%;
}

h1 {
    padding-bottom: 0.3em;
    line-height: 1.2;
    border-bottom: 2px solid #2f51b4;
    position: relative;
    padding-left: 18px;
}

h1:before {
    background: #2f51b4;
    content: "";
    height: 28px;
    width: 8px;
    left: 0;
    position: absolute;
    top: 3px;
}

h2 {
    padding-bottom: 0.3em;
    line-height: 1.2;
    /* border-bottom: 1px solid #2f51b4; */
    position: relative;
    padding-left: 18px;
    /*margin-left: 16px;*/
}

h2:before {
    background: #2f51b4;
    content: "";
    height: 20px;
    width: 5px;
    left: 0px;
    position: absolute;
    top: 3px;
}

h3 {
    padding-bottom: 0.3em;
    line-height: 1.2;
    /* border-bottom: 1px solid #2f51b4; */
    position: relative;
    padding-left: 18px;
    /*margin-left: 16px;*/
}

h3:before {
    background: #00aa00;
    content: "";
    height: 20px;
    width: 5px;
    left: 0px;
    position: absolute;
    top: 3px;
}
</style>

<a id="markdown-外部エンジンを将棋神やねうら王myshogiで使う方法" name="外部エンジンを将棋神やねうら王myshogiで使う方法"></a>
# 外部エンジンを将棋神やねうら王/MyShogiで使う方法

<!-- TOC -->

1. [外部エンジンを将棋神やねうら王/MyShogiで使う方法](#外部エンジンを将棋神やねうら王myshogiで使う方法)
    1. [Step 1. 読み込みたいエンジンに一番近い思考エンジンを選びます。](#step-1-読み込みたいエンジンに一番近い思考エンジンを選びます)
        1. [通常対局エンジンの場合](#通常対局エンジンの場合)
            1. [通常対局エンジン - やねうら王系](#通常対局エンジン---やねうら王系)
            2. [通常対局エンジン - Apery系](#通常対局エンジン---apery系)
            3. [通常対局エンジン - 技巧系](#通常対局エンジン---技巧系)
            4. [通常対局エンジン - それ以外](#通常対局エンジン---それ以外)
        2. [詰将棋エンジンの場合](#詰将棋エンジンの場合)
            1. [詰将棋エンジン - やねうら王系](#詰将棋エンジン---やねうら王系)
            2. [詰将棋エンジン - 脊尾詰](#詰将棋エンジン---脊尾詰)
            3. [詰将棋エンジン - なのは詰め](#詰将棋エンジン---なのは詰め)
            4. [詰将棋エンジン - その他の詰将棋用エンジン](#詰将棋エンジン---その他の詰将棋用エンジン)
    2. [Step 2. 入力欄を適宜、書き換えます。](#step-2-入力欄を適宜書き換えます)
        1. [Step 2.の「エンジンファイル名」](#step-2のエンジンファイル名)
            1. [CPU名とは？](#cpu名とは)
        2. [対応CPUのチェックボックスにチェックを入れます。](#対応cpuのチェックボックスにチェックを入れます)
        3. [用意した思考エンジンの実行ファイルのファイル名を変更する](#用意した思考エンジンの実行ファイルのファイル名を変更する)
        4. [「エンジン表示名」に、そのソフトのわかりやすい名前を入れます。](#エンジン表示名にそのソフトのわかりやすい名前を入れます)
        5. [「エンジン説明1行」「エンジン説明3行」に、そのソフトのエンジンの説明を書きます。](#エンジン説明1行エンジン説明3行にそのソフトのエンジンの説明を書きます)
        6. [「1手10万ノードのR」に値を入れます](#1手10万ノードのrに値を入れます)
        7. [「EvalMemory」に評価関数を読み込むのに必要なメモリサイズを設定します。](#evalmemoryに評価関数を読み込むのに必要なメモリサイズを設定します)
    3. [Step 3. 「エンジン定義ファイルの書き出し」を行います。](#step-3-エンジン定義ファイルの書き出しを行います)
    4. [Step 4. 思考エンジンの入ったフォルダを配置します。](#step-4-思考エンジンの入ったフォルダを配置します)
        1. [思考エンジンのフォルダの配置先のフォルダ](#思考エンジンのフォルダの配置先のフォルダ)
            1. [代表的な思考エンジンの実行ファイル名](#代表的な思考エンジンの実行ファイル名)
            2. [バナー画像について](#バナー画像について)
    5. [Step 5. お疲れさまでした](#step-5-お疲れさまでした)
    6. [Step 6. おまけ](#step-6-おまけ)
        1. [engine_define.xmlの再編集について](#engine_definexmlの再編集について)
        2. [思考エンジンの表示される順序](#思考エンジンの表示される順序)

<!-- /TOC -->

<a id="markdown-step-1-読み込みたいエンジンに一番近い思考エンジンを選びます" name="step-1-読み込みたいエンジンに一番近い思考エンジンを選びます"></a>
## Step 1. 読み込みたいエンジンに一番近い思考エンジンを選びます。

読み込みたいエンジンに一番近いと思われる思考エンジンを選びます。

思考エンジンには、通常対局用と詰将棋エンジンとの二種類が存在します。
- 両方を兼ねているものもありえますが、本ソフトではそれらは別個のものとして扱います。

<a id="markdown-通常対局エンジンの場合" name="通常対局エンジンの場合"></a>
### 通常対局エンジンの場合 

<a id="markdown-通常対局エンジン---やねうら王系" name="通常対局エンジン---やねうら王系"></a>
#### 通常対局エンジン - やねうら王系

やねうら王を改造して作られているものは、Step 1.で「やねうら系」を選びましょう。

やねうら王系の代表的なバリエーションとして以下の思考エンジンがあります。

| ソフト名 | ダウンロード先 | 大会成績など |
| ---- | ---- | ---- | 
| やねうら王 | [https://github.com/yaneurao/YaneuraOu)](https://github.com/yaneurao/YaneuraOu) | WCSC29優勝 |
| elmo | [https://mk-takizawa.github.io/elmo/howtouse_elmo.html](https://mk-takizawa.github.io/elmo/howtouse_elmo.html) | WCSC27優勝 |
| Kristallweizen | [https://github.com/Tama4649/Kristallweizen/](https://github.com/Tama4649/Kristallweizen/) | WCSC28優勝 | WCSC29準優勝 |
| tanuki- | [https://github.com/nodchip/tanuki-](https://github.com/nodchip/tanuki-) | WCSC29 3位 |
| 水匠 | [https://twitter.com/tayayan_ts/status/1258188718759768065](https://twitter.com/tayayan_ts/status/1258188718759768065) | WOCSC30優勝 |
| Qhapaq | [https://github.com/qhapaq-49/qhapaq-bin/releases](https://github.com/qhapaq-49/qhapaq-bin/releases) | WCSC29 5位 |
| dolphin | [https://twitter.com/_illqha](https://twitter.com/_illqha) | 草の根で人気 |

<a id="markdown-通常対局エンジン---apery系" name="通常対局エンジン---apery系"></a>
#### 通常対局エンジン - Apery系

『Apery』か、『Apery』を改造して作られているものは、Step 1.で「Apery系」を選びましょう。

| ソフト名 | ダウンロード先 | 大会成績など |
| ---- | ---- | ---- | 
| Apery | [https://hiraokatakuya.github.io/apery/](https://hiraokatakuya.github.io/apery/) | WCSC28 3位 |

<a id="markdown-通常対局エンジン---技巧系" name="通常対局エンジン---技巧系"></a>
#### 通常対局エンジン - 技巧系

『技巧』か、『技巧』を改造して作られているものは、Step 1.で「技巧系」を選びましょう。

| ソフト名 | ダウンロード先 | 大会成績など |
| ---- | ---- | ---- | 
| 技巧 | [https://github.com/gikou-official/Gikou/](https://github.com/gikou-official/Gikou/) | WCSC26 2位 , WCSC27 3位 |

<a id="markdown-通常対局エンジン---それ以外" name="通常対局エンジン---それ以外"></a>
#### 通常対局エンジン - それ以外

上記以外の通常対局エンジンの場合、Step 1.で「その他の通常対局用エンジン」を選びましょう。

本ソフトから用いる思考エンジンは、USIプロトコルに対応している必要があります。

- 有志が作って公開している将棋の思考エンジンはたいていUSIプロトコルに対応しています。

やねうら王系、Apery系以外で有名なところでは、以下のような通常対局用エンジンがあります。

| ソフト名 | ダウンロード先 | 大会成績など |
| ---- | ---- | ---- | 
| GPSshogi | [https://gps.tanaka.ecc.u-tokyo.ac.jp/gpsshogi/](https://gps.tanaka.ecc.u-tokyo.ac.jp/gpsshogi/) | WCSC22 優勝 |
| うさぴょん2 | [http://usapyon.game.coocan.jp/usapyon2/](http://usapyon.game.coocan.jp/usapyon2/) | SDT4 12位 |

<a id="markdown-詰将棋エンジンの場合" name="詰将棋エンジンの場合"></a>
### 詰将棋エンジンの場合

<a id="markdown-詰将棋エンジン---やねうら王系" name="詰将棋エンジン---やねうら王系"></a>
#### 詰将棋エンジン - やねうら王系

やねうら王系の詰将棋エンジンの場合は、Step 1.で「やねうら王詰め」を選びましょう。

- 『tanuki-詰将棋エンジン』もやねうら王系の詰将棋エンジンで、やねうら王のGitHubからダウンロードできます。

| ソフト名 | ダウンロード先 | 大会成績など |
| ---- | ---- | ---- | 
| やねうら王のGitHub | [https://github.com/yaneurao/YaneuraOu)](https://github.com/yaneurao/YaneuraOu) | WCSC29優勝 |

<a id="markdown-詰将棋エンジン---脊尾詰" name="詰将棋エンジン---脊尾詰"></a>
#### 詰将棋エンジン - 脊尾詰

詰将棋エンジンとして昔から有名なのは『脊尾詰』でしょう。

以下のところからダウンロードできます。

- 『脊尾詰』を使う場合は、Step 1.で「脊尾詰」を選びましょう。

| ソフト名 | ダウンロード先 | 大会成績など |
| ---- | ---- | ---- |
| 脊尾詰 | [http://panashogi.web.fc2.com/seotsume.html](http://panashogi.web.fc2.com/seotsume.html) | 脊尾詰ダウンロード 将棋所/ShogiGUI対応版 | 

<a id="markdown-詰将棋エンジン---なのは詰め" name="詰将棋エンジン---なのは詰め"></a>
#### 詰将棋エンジン - なのは詰め

長手数の詰将棋が解ける詰将棋エンジンとしては、『なのは詰め』も有名でしょう。

- 『なのは詰め』を使う場合は、Step 1.で「脊尾詰」を選びましょう。

| ソフト名 | ダウンロード先 | 大会成績など |
| ---- | ---- | ---- |
| なのは詰め | [http://vivio.blog.shinobi.jp/...](http://vivio.blog.shinobi.jp/%E3%82%B3%E3%83%B3%E3%83%94%E3%83%A5%E3%83%BC%E3%82%BF%E5%B0%86%E6%A3%8B/%E3%81%AA%E3%81%AE%E3%81%AF%E8%A9%B0%E3%82%8164bit%E7%89%88) | なのは詰め64bit版 |

<a id="markdown-詰将棋エンジン---その他の詰将棋用エンジン" name="詰将棋エンジン---その他の詰将棋用エンジン"></a>
#### 詰将棋エンジン - その他の詰将棋用エンジン

その他の詰将棋エンジンの場合、Step 1.で「その他の詰将棋用エンジン」を選びましょう。

<a id="markdown-step-2-入力欄を適宜書き換えます" name="step-2-入力欄を適宜書き換えます"></a>
## Step 2. 入力欄を適宜、書き換えます。

Step 1.で近い思考エンジンを選択すれば、Step 2.の空欄(テキストボックスなど)に自動的に記入されます。これを適宜書き換えます。

<a id="markdown-step-2のエンジンファイル名" name="step-2のエンジンファイル名"></a>
### Step 2.の「エンジンファイル名」

「エンジンファイル名」のところには、エンジンのファイル名を書きます。

ただし、
- 拡張子は書きません。
- ファイル名のうち、CPU名のところは省略して書きます。

例) 実行ファイル名が"YaneuraOu_avx2.exe"であるなら、「_avx2」の部分はこの実行ファイルが対応しているCPUの名前ですから、「エンジンファイル名」のところには、"YaneuraOu"と書きます。

CPU名については、次の説明をご覧ください。

<a id="markdown-cpu名とは" name="cpu名とは"></a>
#### CPU名とは？

いまどきの将棋エンジンは、各CPUごとに最適化した実行ファイルを用意することが多いです。

本ソフトがサポートする思考エンジンの種類として、次の5つがあります。

| 対応CPU | 内容 | OS |
| :---- | :----: | :----: |
| NO SSE | SSEなし用 | 32bit OS用 |
| SSE2 |SSE2 命令を使用 | 64bit OS用 |
| SSE4.1 |SSE4.1 命令を使用 | 64bit OS用 |
| SSE4.2 |SSE4.2 命令を使用 | 64bit OS用 |
| AVX2 |AVX2 命令を使用 | 64bit OS用 |

- AVX2命令に対応したCPUでは、SSE 2命令、SSE4.2命令とSSE4.1命令が使えます。つまり、AVX2命令に対応したCPUでは、NO SSE用の実行ファイル、SSE2用の実行ファイル、SSE4.2用の実行ファイルとSSE4.1用、AVX2用と上記の5種類すべての実行ファイルが実行できます。

集合の関係で言うと、以下のようになっています。(わからなければ読み飛ばしてください)
- NO SSE ⊂ SSE2 ⊂ SSE4.1 ⊂ SSE4.2 ⊂ AVX2

例えば、ご自分のPCのCPUがSSE4.2に対応していて、AVX2に対応していないのでしたら、NO SSE か SSE2 、SSE4.1、SSE4.2用のいずれかの思考エンジンの実行ファイルを用意する必要があります。

<a id="markdown-対応cpuのチェックボックスにチェックを入れます" name="対応cpuのチェックボックスにチェックを入れます"></a>
### 対応CPUのチェックボックスにチェックを入れます。

用意できた思考エンジンの実行ファイルの種類に応じて、「対応CPU」に配置されているチェックボックスにチェックを入れていきます。
実行ファイルは、次のような名前になっている必要があります。

<a id="markdown-用意した思考エンジンの実行ファイルのファイル名を変更する" name="用意した思考エンジンの実行ファイルのファイル名を変更する"></a>
### 用意した思考エンジンの実行ファイルのファイル名を変更する

- 例えば、NO SSE、SSE2用、SSE4.1用、SSE4.2用とAVX2用の5種類の思考エンジンの実行ファイルを用意したとします。それぞれを次のようにファイル名を変更します。

| 実行ファイル名 | 内容 |
| :----: | :----: |
| YaneuraOu_nosse.exe  | SSEなし、32bit OS用 | 
| YaneuraOu_sse2.exe   | SSE2命令を使用、64bit OS用 | 
| YaneuraOu_sse41.exe | SSE4.1命令を使用、64bit OS用 |
| YaneuraOu_sse42.exe | SSE4.2命令を使用、64bit OS用 |
| YaneuraOu_avx2.exe | (AVX2命令を使用、64bit OS用 |

- やねうら王系の思考エンジンでは、最初からこの5つをセットにして配布されていることが多いです。
- また、やねうら王系の実行ファイルのファイル名の末尾にはCPUが最初から上のように書いてあることが多いです。
- "YaneuraOu"の部分がすべてのファイルに共通する部分なので、この場合、「エンジンファイル名」のところには、"YaneuraOu"と書きます。その直後の"_"(アンダーバー)は、「エンジンファイル名」のところには書かないでください。

やねうら王以外の代表的な思考エンジンのエンジンファイル名の変更例は後述します。

<a id="markdown-エンジン表示名にそのソフトのわかりやすい名前を入れます" name="エンジン表示名にそのソフトのわかりやすい名前を入れます"></a>
### 「エンジン表示名」に、そのソフトのわかりやすい名前を入れます。

「エンジン表示名」には、そのソフトのわかりやすい名前を入れます。ここで入力した名前がエンジン名として思考ウインドウなどにそのまま表示されます。

<a id="markdown-エンジン説明1行エンジン説明3行にそのソフトのエンジンの説明を書きます" name="エンジン説明1行エンジン説明3行にそのソフトのエンジンの説明を書きます"></a>
### 「エンジン説明1行」「エンジン説明3行」に、そのソフトのエンジンの説明を書きます。

- 「エンジン説明1行」に、そのエンジンの説明を1行程度で書きます。
- 「エンジン説明3行」に、そのエンジンの説明を3行程度で書きます。

ここで書いた説明文は、エンジン選択の時の説明文として表示されます。

<a id="markdown-1手10万ノードのrに値を入れます" name="1手10万ノードのrに値を入れます"></a>
### 「1手10万ノードのR」に値を入れます

この項目は、1手を10万局面読ませる設定にしたときのR(レーティング : 棋力)を記入します。

- 詰将棋エンジンのときは、この値は無視されます。
- 強さは将棋倶楽部24での強さとします。
- ここで設定した数値に基づいて、各段位用のプリセットを用意します。
    - 例えば、この数値を「1500」(初段相当)と設定した場合、本ソフトで「初段」を選んだ時には、1手につき10万局面を調べる設定になります。
    - いまどきの(最先端の)将棋AIである場合、1手につき10万局面を調べる場合、「3000」(八段)相当のようです。
    - よくわからなければ、この項目は「3000」としておけばそんなに外れた値ではないはずです。

<a id="markdown-evalmemoryに評価関数を読み込むのに必要なメモリサイズを設定します" name="evalmemoryに評価関数を読み込むのに必要なメモリサイズを設定します"></a>
### 「EvalMemory」に評価関数を読み込むのに必要なメモリサイズを設定します。

ここには、評価関数に使用するメモリをMB単位で設定します。

現在主流の評価関数と、それに対応する標準的なサイズ。
- KPPT型 : 「850」程度を設定すると良いでしょう。
- KPP_KKPT型 : 「480」程度を設定すると良いでしょう。
- NNUE型 : 「200」程度を設定すると良いでしょう。

また、USI_Hashで指定するメモリはここに含める必要はありません。

思考エンジン本体が使用する「評価関数用とUSI_Hash用」以外のメモリもここに含める必要はありません。

- 思考エンジン本体が使用する「評価関数用とUSI_Hash用」以外のメモリは固定で200MBとみなされます。
- 200MBでもし不足する場合は、上のEvalMemoryのほうにその不足分を加算した値を設定する必要があります。

<a id="markdown-step-3-エンジン定義ファイルの書き出しを行います" name="step-3-エンジン定義ファイルの書き出しを行います"></a>
## Step 3. 「エンジン定義ファイルの書き出し」を行います。

「エンジン定義ファイルの書き出し」のボタンを押して、エンジン定義ファイルを書き出します。

- エンジン定義ファイルは、"engine_define.xml"というファイル名固定です。このファイル名を変更しないでください。

ここで書き出されたファイルは、思考エンジンの入っているフォルダに配置します。

<a id="markdown-step-4-思考エンジンの入ったフォルダを配置します" name="step-4-思考エンジンの入ったフォルダを配置します"></a>
## Step 4. 思考エンジンの入ったフォルダを配置します。

思考エンジン本体は、ドキュメントフォルダに
myshogi-engines/
というフォルダを作成し、そこにさらに思考エンジン名でフォルダを作成します。

<a id="markdown-思考エンジンのフォルダの配置先のフォルダ" name="思考エンジンのフォルダの配置先のフォルダ"></a>
### 思考エンジンのフォルダの配置先のフォルダ

ドキュメントフォルダのなかに"myshogi-engines"というフォルダを作成します。

- "myshogi-engines"と末尾に複数形の"s"がつくので注意してください。
- ドキュメントフォルダは、Windows 10では、エクスプローラーで見たときに"ドキュメント"と書かれているフォルダです。
- ドキュメントフォルダは、Windows 10では、普通は、"C:\Users\ユーザー名\Documents"です。
- 以下では、ドキュメントフォルダのことを"Documents"と書きます。

いま、"Documents"フォルダのなかに"myshogi-engines"というフォルダを作成するので、このフォルダのことを"Documents/myshogi-engines"と表記します。("/"はその配下のフォルダを表わす記号です。)

次に、"Documents/myshogi-engines"の配下に思考エンジンのフォルダを配置します。

例えば、Aperyであるなら、

- Documents/myshogi-engines/apery/

のようにフォルダを作成します。(このフォルダ名は任意のもので構いません)

このなかにAperyの実行ファイルを入れます。配置するときにファイル名をどのCPUに対応しているかをつけた名前に適宜変更します。

例) Aperyの場合

| 実行ファイルの配置フォルダとファイル名 | 内容 |
| ---- | ---- |
| Documents/myshogi-engines/apery/apery_nosse.exe | 32bit版 |
| Documents/myshogi-engines/apery/apery_sse2.exe  | 64bit版 SSE2以上用 |
| Documents/myshogi-engines/apery/apery_sse41.exe | 64bit版 SSE4.1以上用 |
| Documents/myshogi-engines/apery/apery_sse42.exe | 64bit版 SSE4.2以上用 |
| Documents/myshogi-engines/apery/apery_avx2.exe | 64bit版 AVX2以上用 |
| Documents/myshogi-engines/Apery/engine_define.xml | エンジン定義ファイル |
| Documents/myshogi-engines/Apery/banner.png | バナー画像(任意) |

そのあと、Step 3.で書き出されたエンジン定義ファイルを思考エンジン本体があるフォルダに移動させます。

このファイル名は"engine_define.xml"固定です。本ソフトで書き出したファイルのファイル名を変更しないでください。


<a id="markdown-代表的な思考エンジンの実行ファイル名" name="代表的な思考エンジンの実行ファイル名"></a>
#### 代表的な思考エンジンの実行ファイル名

以下に代表的なソフトでどのように名前を変更すれば良いか書いておきます。

例) 技巧２の場合

| 実行ファイルの配置フォルダとファイル名 | 内容 | 説明 |
| ---- | ---- | ---- |
| Documents/myshogi-engines/gikou2/gikou2_sse42.exe | 64bit版 SSE4.2以上用 | 技巧２は、SSE4.2以上用しか配布されていないので、この名前に変更すると良いです。|

例) 脊尾詰めの場合
| 実行ファイルの配置フォルダとファイル名 | 内容 | 説明 |
| ---- | ---- | ---- |
| myshogi-engines/seotsume/seotsume_nosse.exe | 32bit版 | 脊尾詰めは、32bit版しか配布されていないのでこの名前に変更すると良いです。|

例) なのは詰めの場合
| 実行ファイルの配置フォルダとファイル名 | 内容 | 説明 |
| ---- | ---- | ---- |
| Documents/myshogi-engines/NanohaTsume/NanohaTsumeUSI_sse41.exe | 64bit版SSE4.1以上用 | なのは詰め、64bit版(元ファイル名 "NanohaTsumeUSIx64_popcnt.exe") |
| Documents/myshogi-engines/NanohaTsume/NanohaTsumeUSI_sse2.exe | 64bit版SSE2以上用 | なのは詰め、64bit版(元ファイル名 "NanohaTsumeUSIx64.exe") |
| Documents/myshogi-engines/NanohaTsume/NanohaTsumeUSI_nosse.exe | 32bit版 | なのは詰め、32bit版(元ファイル名 "NanohaTsumeUSI.exe") |

例) それ以外の場合、例えば、64bit版のSSE4.1用の実行ファイルしか配布されていない場合

| 実行ファイルの配置フォルダとファイル名 | 内容 | 説明 |
| ---- | ---- | ---- |
| Documents/myshogi-engines/usi_engine/usi_engine_sse41.exe | 64bit版SSE4.1以上用 | このように、ファイル名の末尾に「sse4_1」とつけて、かつ、Step 2.のチェックボックスでSSE4.2にだけチェックを入れてください。なお、この実行ファイルは、SSE4.2命令をサポートしたCPUでしか動作しません。|

<a id="markdown-バナー画像について" name="バナー画像について"></a>
#### バナー画像について

あと、思考エンジンの実行ファイルを配置したフォルダにバナー画像も用意してあげると、本ソフトで思考エンジンを選択するときにそれが表示されます。(なければ"NO BANNER"と表示されるだけです。なくても動作には問題ありません。)

バナー画像のファイル名は"banner.png"固定です。画像サイズは、横512px × 縦160pxでPNG形式で用意します。例えばAperyの場合であれば、さきほどの例のようにフォルダを作成していたなら、次の場所に配置することになります。

- Documents/myshogi-engines/apery/banner.png

思考エンジンが用いる評価関数は、その思考エンジンが読み込めるように配置します。例えば、Aperyであれば、同じフォルダのなかに"eval"というフォルダを作成してそこに配置するはずです。(各思考エンジンに合わせた配置の仕方をしてください。)

- Documents/myshogi-engines/apery/eval/…

<a id="markdown-step-5-お疲れさまでした" name="step-5-お疲れさまでした"></a>
## Step 5. お疲れさまでした

将棋神やねうら王/MyShogiでは、起動時にこのmyshogi-enginesというフォルダ配下のすべてのフォルダに対してengine_define.xmlを探して、このファイルがあれば、そのフォルダを思考エンジンが格納されているフォルダとみなします。

そこで、以上のように配置し、将棋神やねうら王を起動すれば思考エンジン選択の画面に表示されるという仕組みです。

<a id="markdown-step-6-おまけ" name="step-6-おまけ"></a>
## Step 6. おまけ

ここでは、より進んだ設定をする方法について説明しておきます。

<a id="markdown-engine_definexmlの再編集について" name="engine_definexmlの再編集について"></a>
### engine_define.xmlの再編集について

一度書き出した"engine_define.xml"を再度編集する機能は本ソフトには用意されていません。

しかし、メモ帳やテキストエディタで直接このファイルを開いて、ちょっとした編集を行うことはできます。もし「実行ファイル名やエンジンの説明をちょっと編集したいな…」という場合には、そのように直接編集することができます。

<a id="markdown-思考エンジンの表示される順序" name="思考エンジンの表示される順序"></a>
### 思考エンジンの表示される順序

エンジン選択画面では、"DisplayOrder"が大きい順番で表示することになっています。

- "engine_define.xml"上のこの値を直接編集してください。
- 『将棋神やねうら王』では、10000～10099番を使用しています。
- 『将棋神やねうら王２』では、20000～20099番を使用しています。
- このダイアログで書き出した"engine_define.xml"は、99999番固定になります。好きな値に調整してください。99999番になるので、思考エンジンの選択画面では、一番末尾に表示されるはずです。

以上