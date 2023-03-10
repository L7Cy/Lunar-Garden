---
title: はじめてのAnki – まず使ってみる  the right stuffを読む
tags: [2023/02/11,]
aliases: []
---

[[やれたらやる]]
source: [はじめてのAnki – まず使ってみる | the right stuff](https://rs.luminousspice.com/how-to-anki/)
author: 

> ## Excerpt
> 分散学習システム Anki を今すぐ使い始めるのに最低限必要な使い方を紹介します。最新版 Anki 2.0.35 に準拠しています。Ankiをダウンロードして、記憶するカードを作成し、学習してみましょう。画像や動画、音声を追加する方法、学習中に音声ファイルを再生する方法も取り上げています。

---
**連載: Ankiの使い方 〜覚えるために忘れろ〜 第1回**

Ankiを始めたいけど、何から始めて良いか分からない方のためにこの記事を書きました。インストールから、問題作成、学習までの基本的な使い方の流れになれていきましょう。Ankiを使っている人なら誰でも知っていて、常に使っている機能、マニュアルにも当然書いてある機能を説明しています。

画像や動画、音声を追加する方法、学習中に音声ファイルを再生する方法も取り上げています。

この記事の内容

1.  [この記事を読む前に](https://rs.luminousspice.com/how-to-anki/#i-0)
2.  [どんなソフトなの](https://rs.luminousspice.com/how-to-anki/#i-1)
3.  [入手方法](https://rs.luminousspice.com/how-to-anki/#i-2)
4.  [言語設定](https://rs.luminousspice.com/how-to-anki/#i-3)
5.  [起動直後に開くメインウィンドウ](https://rs.luminousspice.com/how-to-anki/#i-4)
6.  [問題の登録](https://rs.luminousspice.com/how-to-anki/#i-5)
7.  [登録したカードの確認](https://rs.luminousspice.com/how-to-anki/#i-6)
8.  [新規の問題を学習](https://rs.luminousspice.com/how-to-anki/#i-7)
9.  [復習する](https://rs.luminousspice.com/how-to-anki/#i-8)
10.  [学習を中断するには](https://rs.luminousspice.com/how-to-anki/#i-9)
11.  [出題上限の変更](https://rs.luminousspice.com/how-to-anki/#i-10)
12.  [単語帳オプションの変更](https://rs.luminousspice.com/how-to-anki/#i-11)
13.  [おわりに](https://rs.luminousspice.com/how-to-anki/#i-12)
14.  [この連載について](https://rs.luminousspice.com/how-to-anki/#i-13)
15.  [Ankiの使い方になれるためのボット](https://rs.luminousspice.com/how-to-anki/#i-14)
16.  [もっと深く知りたい](https://rs.luminousspice.com/how-to-anki/#i-15)
17.  [更新情報](https://rs.luminousspice.com/how-to-anki/#i-16)

この情報は、デスクトップ PC 版 Anki 2.0.35 (Mac OS X) に基づいて作成しています。 他のプラットフォーム版をお使いの方は、適宜読み替えてください。

特に PC 版と、iOS アプリ AnkiMobile や Android(アンドロイド)アプリ AnkiDroid の間では、データの互換性はありますが、ユーザーインターフェイスや機能に違いがあります。

### iOS アプリ向け情報

iPhone や iPad などで AnkiMobile をお使いの方は、[iPhone ユーザーのためのはじめての Anki](https://rs.luminousspice.com/how-to-use-ankimobile/)をご覧下さい。はじめて使うときに必要な、毎日の学習が続けられる最低限の使い方をまとめました。AnkiMobile だけではできない機能を PC 版 Anki と連携して実現する方法も取り上げています。

### Android アプリ向け情報

AnkiDroid の使い方については、[AnkiDroid 2 取扱説明書](https://ankidroid.org/docs/manual-ja.html)をご覧下さい。

Ankiとは、分散学習(Spaced Repetition)ができるフラッシュカードです。 Ankiでは思い出しやすさで次の復習のタイミングが決まります。覚えにくいカードは頻繁に復習し、簡単に記憶できたカードは時間をあけて記憶を確認します。 このような原則に基づくと効果的な結果が得られるという学習理論に基づいて作られています。 多量のカードを持っていても、結果として一日の復習量は散らばって、負担を軽減してくれます。

忘れてはいけないポイントは、毎日続けることです。中断が頻繁に発生すると分散学習の効果が期待できません。

いつでもどこでも復習しやすいように、Ankiは、Mac、Windows、Linux/BSD、iOS(iphone, ipad, ipod touch)、Androidなどいろいろなシステム上で使うことができ、無料のウェブサービス AnkiWeb を経由して、端末間で学習内容、履歴を同期することができます。 専用のアプリケーションがない端末でもウェブブラウザ機能を持っているなら、AnkiWebにアクセスして直接学習ができます。

Ankiには、ユーザーが作ったデータを共有するコミュニティがあります。 自分でカードを作らなくても共有単語帳をダウンロードすればすぐ学習が始められます。また、アドオンを使えば簡単に機能拡張することができます。 もちろん、自分で作った単語帳を共有したり、アドオンと作ってAnkiに機能追加することもできます。

### Anki学習の流れ

まず最初に、Ankiの作者Damien Elmesが作成した、Shared decks and review basics というYouTubeのビデオをご覧ください。

このビデオでは、最初に共有単語帳一覧にアクセスして、単語帳をインストールします。 この単語帳を使って、Ankiの一通りの学習をした後に、単語帳オプションの設定方法について解説する内容です。

<iframe width="420" height="315" src="https://www.youtube-nocookie.com/embed/QS2G-k2hQyg" frameborder="0" allowfullscreen=""></iframe>

説明の英語が分からなくても、全体のAnki学習の流れを感じを掴んでいただけると思います。

Anki2は、[Ankiオフィシャルサイト](http://ankisrs.net/)からMac、Windows、Linux/BSD版がダウンロードできます。モバイルデバイス用のアプリケーションのダウンロード先もこちらで紹介しています。

「[Ankiのインストール](https://rs.luminousspice.com/install_anki/)」では、アプリケーションのダウンロードからインストールまでを利用システム別に簡単に説明しています。ダウンロードサイトの英文に気後れするような方はこちら記事をご覧ください。

ダウンロードファイルを解凍し、最初に起動すると言語設定の画面が出ます。ここでユーザーインターフェースに使いたい言語を選択してください。

![言語設定画面](https://rs.luminousspice.com/images/how2anki_1_1.png)

図 1. 言語設定画面

次に確認ウィンドウを表示しますので、自分が使用したい言語を選択しているか確認してください。

![言語設定 確認ウィンドウ](https://rs.luminousspice.com/images/how2anki_1_15.png)

図 2. 言語設定 確認ウィンドウ

\[No\]を選択すると、先ほどの選択画面に戻ります。

設定した言語は、環境設定画面から変更できます。具体的な方法は、「[Anki2の言語設定を変更する](https://rs.luminousspice.com/how-to-change-lang/)」で紹介しています。

言語設定が終わると、メインウィンドウが開きます(図 3)。なお、次回のAnkiの起動からこの画面が最初に開きます。 メインウィンドウには、使用中の単語帳一覧を表示します。学習中でもウィンドウ上部の\[単語帳\]リンクをクリックすると、この画面に戻ります。

![初回起動直後のメインウィンドウ](https://rs.luminousspice.com/images/how2anki_1_2.png)

図 3. 初回起動直後のメインウィンドウ

`Default` という単語帳があるのがわかります。`Default` 単語帳は特殊な単語帳で削除することが出来ません。また、`Default` の中身が空の場合、他の単語帳があれば表示されません。

問題を登録してみましょう。 \[追加\]リンクをクリックすると、ノート追加ウィンドウを表示します。

![問題を登録](https://rs.luminousspice.com/images/how2anki_1_3.png)

図 4. ノート追加ウィンドウで問題を登録

Frontフィールドには表面に表示する問題を、Backフィールドには裏面に表示する解答を入力します。\[追加\]ボタンを押すとフィールドに入力した問題を登録します。ここで登録した一組のデータをAnkiでは **ノート** と呼びます。

Ankiでは、ノートのデータをHTMLを使って書式設定できます。ノートエディタのフィールドは、WYSIWYGエディタの機能を持っていますので、ウィンドウ上部のボタンを使って文字の装飾をしたり、メディアファイルを追加したりできます。HTMLを直接編集するには、ショートカット(Mac OS X: Command+Shift+X, Windows: Ctrl+Shift+X)を使って HTML エディタを呼び出します。

既定ではDefaultという名前の単語帳にこの問題を追加します。保存先を変更するには、ウィンドウ右上の\[Default\]ボタンを押します(図3)。

### 画像、音声、動画の登録方法

表面(質問)、裏面(解答)ともにメディアファイル(画像、音声、動画)を読み込むことができます。

一番簡単な方法は、メディアファイルを読み込みたいフィールドにドラッグアンドドロップすることです。ウェブブラウザに表示している画像をAnkiに直接ドロップすることもできます。コピーアンドペーストでに取り込むことも可能です。

また、Frontフィールド、Backフィールドにカーソルを合わせて、追加ウィンドウの上部のボタンの並びから\[クリップの画像\]ボタン (Mac OS X: fn+F3, Windows: F3) を押して現れた画面からメディアファイルを選択して読み込むこともできます。

![メディアを登録](https://rs.luminousspice.com/images/how2anki_1_12.png)

図 5. メディアを登録

上の例では画像と、`ripple.mp3` という名前の音声ファイルを読み込んだところです。

問題を全て登録し終わったら、今度は問題を出題させてみましょう。 \[閉じる\]ボタンを押して追加ウィンドウを閉じると、元のホームページに戻ります。

### テキストの読み上げ

音声ファイルを用意するのではなく、フィールドのテキストをPCに読んでもらう (発音する) こともできます。それにはAwesomeTTSというアドオンファイルが必要になります。具体的な設定方法は、[Ankiの共有リソースを使ってみる](https://rs.luminousspice.com/how-to-use-shared-resources/)で紹介しています。

フィールドは追加削除、名前の変更もできます。また、[カードを編集すると表面、裏面のどこに表示するか設定](https://rs.luminousspice.com/how-to-edit-cards/)できます。またカードに表示しないフィールドを設定することもできます。 [CSVファイル形式などに保存した複数の問題を一括で読み込む](https://rs.luminousspice.com/how-to-import/)ことができます。

Anki は、一日の学習の上限値20を設定しているので、20以上登録した場合は、このあとすぐに学習をはじめても全部のカードを見ることが出来ません。

登録したカードを確認したい場合は、[ブラウザーのプレビュー機能](https://rs.luminousspice.com/browser-overview/)を利用すると便利です。

ホームページの単語一覧から単語帳を選択すると、その単語帳のトップページを表示します。 この画面では、単語帳の概要と学習キューに入っているカードの内訳を表示します。

![単語帳のトップページ](https://rs.luminousspice.com/images/how2anki_1_4.png)

図 6. 単語帳のトップページ

上の例では、新規に学習するカードが6枚学習キューに入っていることを示しています。 ここで\[学習する\]ボタンを押すと、学習セッションを開始し、問題を表示します。

### 学習の進め方

![出題画面](https://rs.luminousspice.com/images/how2anki_1_5.png)

図 7. 出題画面

\[解答を表示\]ボタンを押すと、罫線をはさんで問題と解答が現れます。

![解答表示](https://rs.luminousspice.com/images/how2anki_1_6.png)

図 8. 解答表示

ウィンドウの下中央に3つのボタンの中から、記憶状態に応じてボタンを選択するとこのカードの学習は終了します。

-   \[もう一回\]ボタンは、忘れてしまった時に押します。ボタンの上に表示した時間後に再度出題します。既定では1分後です。解答を記憶し直しましょう。
    
-   \[普通\]ボタンは、覚えていた場合に押します。既定では10分後に再度出題します。
    
-   \[簡単\]ボタンは、覚えていて簡単に感じた場合に押します。このボタンを押すとこのカードの学習は終了し、既定では4日後に復習が設定します。
    

問題を解答していき、全ての問題の復習期日を翌日以降に設定したところで、その日の学習が終了します。

![一日の学習終了](https://rs.luminousspice.com/images/how2anki_1_7.png)

図 9. 一日の学習終了

### 音声ファイルの再生方法

既定の設定では、音声ファイルは自動再生する設定になっています。もし、自動再生しない場合は、単語帳のオプション設定を確認してみてください。

単語帳のオプション設定は、メインウィンドウの単語帳一覧から設定したい単語帳をクリックし、画面下の\[オプション\]ボタンを押すか、キーボードの\[O\]を押してください。

![音声ファイルについての単語帳のオプション設定](https://rs.luminousspice.com/images/how2anki_1_13.png)

図 10. 音声ファイルについての単語帳のオプション設定

一度再生した音声ファイルをもう一度聴きたい場合は、キーボードの\[R\]を押すか、画面右下のドロップダウンリスト\[もっと\]から、\[オーディオを再生\]を選択してください。

![音声ファイルの再生](https://rs.luminousspice.com/images/how2anki_1_14.png)

図 11. 音声ファイルの再生

### 学習の上限

Anki は、一日の学習枚数に上限を設定しています。初期設定は20で、20枚以上カードを追加しても、初日の学習は20枚です。残りのカードは翌日以降に繰り返します。

既定では、普通と答えた場合の新規カードの復習期日は1日後です。一日経ったらAnkiを起動し、単語帳一覧から単語帳Default(保存指定した単語帳)をクリックして、出題してみましょう。前の日に学習した問題を出題します。

![復習問題の解答画面](https://rs.luminousspice.com/images/how2anki_1_9.png)

図 12. 復習問題の解答画面

-   \[もう一回\]ボタンは、忘れてしまった時に押します。ボタンの上に表示した時間後に再度出題します。既定では10分後です。解答を記憶し直しましょう。
    
-   \[難しい\]ボタンは、覚えていて難しく感じた場合に押します。
    
-   \[普通\]ボタンは、覚えていた場合に押します。
    
-   \[簡単\]ボタンは、覚えていて簡単に感じた場合に押します。
    

正解した場合の次回の復習期日は、過去の学習履歴によって決定します。\[難しい\]を押せば期日は短めに、\[簡単\]を押せば復習期日は長く設定します。

出題カードを全て復習し、復習期日を翌日以降に全て設定すると、その日の学習が終了します。

### 解答ボタンを押し間違えた

学習中よくある失敗が、間違ったボタンを押して、カードの行方が分からなくなってしまうことです。このような時には、落ち着いてメニューバーから\[編集\]>\[取り消す\](Mac OS X: Command+Z, Windows: Ctrl+Z)を選択しましょう。再度出題画面に戻ります。

### 復習の上限

Anki は、一日の復習枚数に上限を設定しています。初期設定は100で、100枚以上のカードが復習期日に達していても、出題数は100枚です。残りのカードは翌日以降に繰り返します。

学習セッションを途中で止める方法を使い分ければ、学習セッションを自分の都合にあわせて分割できるようになります。 Anki学習できる短い時間がもっとたくさん増えるはずです。

### Ankiを終了する

Ankiそのものを終了したいなら、メニューバーから\[ファイル\]>\[終了\](Mac OS: Command+Q, Windows: Ctrl+Q)を選びます。学習セッション中で直接終了しても問題はありません。次回起動した時には、残りのカードを学習できます。

### 学習セッションから抜ける

Ankiを起動したまま、中断したい場合は、ウィンドウ上部の\[単語帳\]リンクをクリックするか、\[D\]キーを押します。学習セッションから抜け出して、起動直後に表示する単語帳一覧に戻ります。

上の2つの方法で中断した後に、その日の内に再開すれば残りのカードを学習できます。再開した時に、一日の上限までカードを取得しなおすことはありません。

翌日以降にセッションを再開した場合は、残りのカードにその日の上限までカードが追加になります。

### 特定のカードだけ学習をやめる

特定のカードだけを学習対象から外して、他のカードはそのまま継続したい場合もあります。画面右下のドロップダウンリスト\[もっと\]から\[ノートを延期\]、\[カードを保留\]、\[ノートを保留\]のいずれか適切なものを選びます(図 11)。この3つの処理の違いについては、[いま表示しているAnkiカードだけ学習をやめる方法](https://rs.luminousspice.com/how-to-suspend-this-card/)で詳しく説明しています。

カードの出題数を変更するには、2通りの方法があります。

-   一時的に上限を変更する場合は、[カスタム学習セッション](https://rs.luminousspice.com/how-to-customize-learning/)を使います。
    
-   変更内容をそのまま使い続けるには、単語帳オプションを変更します。
    

単語帳のトップページ下にある\[オプション\]ボタン(図 6)を押すと、あるいは \[O\]キーを押すと、オプション設定画面が開きます。

### 新規カードの学習オプション

既定の設定は次の通りです。

-   新規の問題の上限は一日20題です。
    
-   新規カードの学習ステップは1分、10分の二段階の設定です。
    
-   新規カードの出題順は追加順です。ランダムに出題するように変更することもできます。
    
-   新規カードの学習後に設定する復習期日は1日後です。
    
-   新規カードで\[簡単\]と選択した場合の復習期日は4日後です。
    

![単語帳のオプション設定](https://rs.luminousspice.com/images/how2anki_1_8.png)

図 13. 単語帳のオプション設定

### 復習カードの学習オプション

既定の設定は次の通りです。

-   復習問題の上限は100題です。
    

![復習のオプション設定](https://rs.luminousspice.com/images/how2anki_1_10.png)

図 14. 復習のオプション設定

### 忘却カードの学習オプション

忘却カードとは復習した時に思い出せなかったカードのことです。

-   忘れた場合の再学習のステップは10分後の一段階です。
    

![忘却のオプション設定](https://rs.luminousspice.com/images/how2anki_1_11.png)

図 15. 忘却のオプション設定

忘却回数が設定値を超えると無駄なカード (Leech) の扱いを受け、保留するか、タグをつけるかどちらかの処理が行われます。

初期設定では\[保留\]に設定され、復習スケジュールから外されます。 [無駄なカード(Leech)になってもAnki学習を続ける方法](https://rs.luminousspice.com/management_of_leeches/)で、復習スケジュールに復帰する方法を説明しています。

Ankiを使うのに最低限必要な操作は以上です。 Ankiが設定した期日通りに復習を進めて行きましょう。 Ankiがスケジュール管理しているので安心して忘れることができます。

Ankiの詳しい機能は、[ユーザーマニュアル](http://ankisrs.net/docs/manual.html)をお読みください。 一部未翻訳の項目が残っていますが、[日本語マニュアル](http://wikiwiki.jp/rage2050/)も参考にしてみてください。

この8回の連載では実際の使用手順に基づいた活用方法を紹介します。 Ankiを使った学習全般を体験できるよう内容を構成しました。 簡単なものから難しいものにステップアップしていく順番に配置しています。

Ankiは、このアプリケーションで特別な意味を持つ用語を多数使用しています。[Anki 用語集](https://rs.luminousspice.com/anki_glossary/)をまとめていますので、もしAnkiを使っている時に意味の分からない用語にであったら、調べてみてください。

はじめてAnkiを使おうとして、何から始めて良いか分からず途方に暮れている人のためにこの連載を書きました。Ankiを使うのに最低限必要な操作を取り上げました。Ankiを使っている人なら誰でも知っていて、常に使っている機能、マニュアルにも当然書いてある機能を説明しています。

この連載で取り上げたAnkiの機能は、[はじめてAnkiを使う人のための索引](https://rs.luminousspice.com/index-how-to-anki/)としてまとめています。調べたい機能が決まっている場合はこの索引も活用してみてください。

Ankiの慣れ親しんで、使い方の感覚が掴めれば、[ユーザーマニュアル](http://ankisrs.net/docs/manual.html)やネット上の情報を活用して、読者の皆さんの専門分野が発揮できるような使い方ができるようになると思います。 学習する教科、分野によって最適な使い方に違いがあるはずです。その時はぜひ皆さんの高度な技を共有してくださいです。

### 連載: Ankiの使い方 〜覚えるために忘れろ〜 記事一覧

1.  はじめてのAnki – まず使ってみる(インストール、問題入力、学習の流れ)
2.  [Ankiにデータをまとめて取り込む](https://rs.luminousspice.com/how-to-import/)(テキストデータの一括登録)
3.  [Ankiの共有リソースを使ってみる](https://rs.luminousspice.com/how-to-use-shared-resources/)(アドオン、共有単語帳)
4.  [Ankiのカード表示を編集する](https://rs.luminousspice.com/how-to-edit-cards/)(カード編集、外部リンク設定、読み上げ)
5.  [Ankiのブラウザーの使い方とデータ検索](https://rs.luminousspice.com/browser-overview/) (ブラウザー、検索条件)
6.  [フィルター単語帳でAnki学習をカスタマイズしよう](https://rs.luminousspice.com/how-to-customize-learning/) (カスタム学習、フィルター単語帳、独自の学習条件を設定)
7.  [Anki統計情報を活用したバックログ解消法](https://rs.luminousspice.com/reduce-anki-backlog-with-stats/)(統計情報の見方、たまった復習カードの解決法)
8.  [Anki単語帳を共有する方法](https://rs.luminousspice.com/how-to-share-anki-decks/) (単語帳の書き出し、AnkiWebへの共有)
9.  [はじめてAnkiを使う人のための索引](https://rs.luminousspice.com/index-how-to-anki/)(連載内容の索引)
10.  [Anki 用語集](https://rs.luminousspice.com/anki_glossary/)(Ankiの基本概念の説明)

ユーザーマニュアルやウェブ上の色々な情報を参考にして、自分独自の使い方を見つけられる程度までAnkiの使い方に慣れていただくのが目標です。

ツイッターアカウント Ankigene (@Ankigene) は、[Anki を使い始めた時に、知っておくと役立つ知識](https://rs.luminousspice.com/ankigene-bot-guide/)を定期的につぶやきます。 事前に基本的な使い方を目にしていれば、いざという時に情報を探す時間を短縮できます。全ての投稿が20日で一周するスケジュールです。

Ankiの具体的な使い方というより、効果を上げるための考え方についての記事を紹介します。

[Anki 日本語ユーザーマニュアル - はじめに](http://wikiwiki.jp/rage2050/?manual#s17ae333)

Ankiのマニュアルの日本語訳の最初の部分ですが、Ankiとはどんな機能を提供するアプリケーションソフトなのか丁寧に説明しています。使い始める前に理解しておきたい内容です。

[決して後退しない学習ーAnkiを使うとどうして一生忘れないのか？](http://readingmonkey.blog45.fc2.com/blog-entry-678.html)

Ankiが提供する分散学習機能について簡単に紹介しています。

[根気も時間もないあなたが外国語習得の臨界点を越える一番ゆるいスタートアップの方法](http://readingmonkey.blog45.fc2.com/blog-entry-666.html)

ゼロから新しい言語を始める方に最適です。Ankiを活用した学習手順を丁寧に解説しています。

[効果的な学習法: 知識を定式化する20個のルール](http://d.hatena.ne.jp/rage2050/20110502)

Ankiに先行する記憶用アプリケーションSuperMemoの作者による効果的な記憶法の解説の日本語訳です。

2013/04/12: 初出

2013/06/11: カードへメディアを登録、音声ファイルの再生方法を追加

2013/09/26: Ankiのインストール方法について情報追加

2013/10/15: 全面改訂

2014/03/24: 言語設定の方法を更新

2014/09/21: 再構成

2015/01/24: スマホアプリの注意点追加

2016/01/16: ノート編集について加筆

2016/04/05: Anki 2.0.35 に基づいて言語設定の方法を更新
