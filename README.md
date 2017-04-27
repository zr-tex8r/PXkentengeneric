PXkentengeneric パッケージバンドル
==================================

LaTeX： (u)pLaTeX で KentenGeneric フォントを利用する

Adobe が配布している圏点用の OpenType フォントである [KentenGeneric] を
(u)pLaTeX で利用するためのパッケージ。

[KentenGeneric]: https://github.com/adobe-fonts/kenten-generic

### 前提環境

  * フォーマット： LaTeX
  * エンジン： pTeX／upTeX
  * DVI ウェア： dvipdfmx／dvips

### インストール

まずはリンク先のサイトから [KentenGeneric] フォントの実体 KentenGeneric.otf
を入手して、次の場所に配置する。
（TDS 1.1 に従ったシステムの場合。）

  - `KentenGeneric.otf` → $TEXMF/fonts/opentype/adobe/

※Windows の場合は、上記の代わりに OS にインストールしてもよい。

その後、本パッケージのファイルを次の場所に移動する。
（TDS 1.1 に従ったシステムの場合。）

  - `*.sty`   → $TEXMF/tex/platex/pxkentengeneric/
  - `*.tfm`   → $TEXMF/fonts/tfm/public/pxkentengeneric/
  - `*.vf`    → $TEXMF/fonts/vf/public/pxkentengeneric/
  - `pdfm-px*.map` → $TEXMF/fonts/map/dvipdfmx/pxkentengeneric/
  - `px*.map` → $TEXMF/fonts/map/dvips/pxkentengeneric/

必要に応じて mktexlsr を実行する。

#### フォントマップ登録（TeX Live）

updmap で登録すればよい。

    updmap-sys --enable KanjiMap pdfm-pxkentengeneric.map
    ('updmap-sys' は適切なコマンド名で置き換える)

#### フォントマップ登録（TeX Live 以外）

［dvipdfmx］

dvipdfmx の設定ファイル `dvipdfmx.cfg` に以下の行を追記する。

    f pdfm-pxkentengeneric.map

［dvips］

常用している設定ファイル（`config.*`）に以下の行を追記する。

    p +pxkentengeneric.map

### ライセンス

MITライセンスの下で配布される。

pxkentengeneric パッケージ ― 本体
----------------------------------

### パッケージ読込

    \usepackage{pxkentengeneric}

### 使用法

次のように、KentenGeneric の圏点文字を出力する命令が用意されている。

    命令               JIS   UCS
    \kentengbullet           2022   黒中点
    \kentengtriangle   2225  25B2   黒三角
    \kentengTriangle   2224  25B3   白三角
    \kentengfisheye          25C9   蛇の目
    \kentengCircle     217B  25CB   白丸
    \kentengbullseye   217D  25CE   二重丸
    \kentengcircle     217C  25CF   黒丸
    \kentengBullet           25E6   白中点
    \kentengsesame           FE45   黒ゴマ点
    \kentengSesame           FE46   白ゴマ点

また、`\kentengfont` 命令で現在の和文フォントが KentenGeneric に切り替わる
ので、これと上の表に記したコード値の文字を書くことでも所望の文字を出力する
ことができる。

    {\kentengfont △}

ただし pLaTeX の場合は JIS コードの無い文字はこの方法では出力できない。

更新履歴
--------

  * Version 0.2  〈2017/04/25〉
      - 最初の公開版

--------------------
Takayuki YATO (aka. "ZR")  
http://zrbabbler.sp.land.to/
