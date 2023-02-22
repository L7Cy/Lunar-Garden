---
title: Karabiner-Elementの設定例について - Qiitaを読む
tags: [2023/02/21,]
aliases: []
---

source: [Karabiner-Elementの設定例について - Qiita](https://qiita.com/s-show/items/40ad22c4ee4a0465fad5)
author: s-show

> ## Excerpt
> Karabiner-Elementsの各設定項目については、Karabiner-Elementsの各設定項目の内容についてでリファレンス的にまとめましたので、こちらの記事は、実現したい機能から設定ファイルの書き方を探せる（要は逆引き）...

---
この記事は最終更新日から3年以上が経過しています。

投稿日 2017年10月08日

更新日 2019年02月03日

Karabiner-Elementsの各設定項目については、[Karabiner-Elementsの各設定項目の内容について](https://qiita.com/s-show/items/a1fd228b04801477729c)でリファレンス的にまとめましたので、こちらの記事は、実現したい機能から設定ファイルの書き方を探せる（要は逆引き）ような記事にしました。

紹介する機能は、以下のとおりです。

-   "control-M"のような組み合わせを別の組み合わせに変換
-   "command-P"のような組み合わせを任意の単独キーに変換
-   "F5"や"Escape"等の単独のキーを"control-O"のような組み合わせに変換
-   特定のキーを無効化する（2018年12月10日追加）
-   任意のキーにマウスクリックを割り当てる
-   任意のキーにコマンド実行を割り当てる
-   1回のキータイプで複数回のキータイプを実現する
-   単独で押した場合とshift等と組み合わせた場合で違う変換を行う
-   "A"を押しながら"B"を押したら"C"に変換する
-   あるキーを押している間は他のキーの動作を変更する（2017年11月23日追加、2019年1月21日タイトル変更）
-   キーの2連打に特定の処理を割り当てる（2017年11月23日追加）
-   Emacsの"control-x control-f"のような2段階のキーストロークを実現する
-   特定のアプリでのみ（またはその反対）変換を実行する（2017年11月23日追加）
-   IMEの状態に応じて処理を変える & IMEの状態を切り替えたい（2017年11月23日追加）
-   マウスクリックに処理を割り当てる（2017年11月23日追加）
-   キーボードでマウス操作を実現する（2019年2月3日追加）
-   文字入力を実現する（2017年11月26日追加）
-   2つ以上のキーの同時押しに処理を割り当てる
-   キーの長押しに処理を割り当てる

なお、原因不明ですが、Karabiner-Elementsは、JISキーボードをUSキーボードと認識することがあります。USキーボードと認識されると、キーキャップに表示されている文字とアプリが認識する文字が異なってしまい、例えば、JISキーボードの"\["が"\]"と認識されたりします。

こうなった場合、頑張ってJISキーボードと認識されるようにあれこれ試してみるか、Karabiner-Elements側の認識に合わせて設定してください（私は後者の方法で対処しました）。

-   Karabiner-Elementsのバージョン: 12.2.0
-   MacOSのバージョン: 10.12.6（macOS Mojave）

なお、その他の設定例や、設定を楽に行う方法も記事にしていますので、そちらもあわせて確認してください。

[Karabiner-Elementsを使ってJISキーボードの"全角/半角"でIMEを切り替える方法 - Qiita](https://qiita.com/s-show/items/08a7c1b558e4d7e6f1b0)  
\[Karabiner-Elementsの設定項目が増えてEmacsライクな設定が楽になった - Qiita\](([https://qiita.com/s-show/items/e83215f4ee10422abd7c](https://qiita.com/s-show/items/e83215f4ee10422abd7c))  
[Karabiner-Elementsでenthumble（Windows App）のような操作を実現する方法 - Qiita](https://qiita.com/s-show/items/0036e45d4b5928569dd9)  
[KE-complex\_modificationsを使ってKarabiner-Elementsの設定を楽にする方法 - Qiita](https://qiita.com/s-show/items/fb788d90faba7eeb9051)

## [](https://qiita.com/s-show/items/40ad22c4ee4a0465fad5#control-m%E3%81%AE%E3%82%88%E3%81%86%E3%81%AA%E7%B5%84%E3%81%BF%E5%90%88%E3%82%8F%E3%81%9B%E3%82%92%E5%88%A5%E3%81%AE%E7%B5%84%E3%81%BF%E5%90%88%E3%82%8F%E3%81%9B%E3%81%AB%E5%A4%89%E6%8F%9B)"control-M"のような組み合わせを別の組み合わせに変換

この設定を行う場合、`"from"`の`"key_code"`と`"modifiers"`の両方を指定します。"control"のような装飾キーは`"modifiers"`に設定し、装飾キーと一緒に押すキー（下の例なら"PageUp"）は`"key_code"`に設定します。

以下の例では、"control-PageUp"を"control-shift-tab"に変換するというものです。`"optional"`にキーを指定していないため、"control-PageUp"では変換が実行されますが、"control-shift-PageUp"では変換が実行されません。この場合、`"optional"`に"shift"を指定すれば、"control-shift-PageUp"でも変換されますし、"caps\_lock"を指定すれば、"caps\_lock"がオンの状態でも変換が実行されますし、"any"を指定すれば"command"や"option"を同時に押していても変換が実行されます。

一方、`"to"`には"control-shift-tab"の組み合わせを指定します。`"from"`と同様に、"control"と"shift"の装飾キーは`"modifiers"`に設定し、"tab"は`"key_code"`に設定します。

```
{
  "description": "control-pageupをcontrol-shift-tabに変換",
  "manipulators": [
    { "type": "basic",
      "from": {
        "key_code": "page_up",
        "modifiers": { "mandatory": [ "control" ] }
      },
      "to": [
        {
          "key_code": "tab",
          "modifiers": [ "control", "shift" ]
        }
      ]
    }
  ]
}
```

## [](https://qiita.com/s-show/items/40ad22c4ee4a0465fad5#command-p%E3%81%AE%E3%82%88%E3%81%86%E3%81%AA%E7%B5%84%E3%81%BF%E5%90%88%E3%82%8F%E3%81%9B%E3%82%92%E4%BB%BB%E6%84%8F%E3%81%AE%E5%8D%98%E7%8B%AC%E3%82%AD%E3%83%BC%E3%81%AB%E5%A4%89%E6%8F%9B)"command-P"のような組み合わせを任意の単独キーに変換

この設定を行う場合、`"from"`の設定は1つの上の例と同様に設定しますが、`"to"`は`"key_code"`だけ設定すればOKです。  
なお、"vk\_launchpad"というコードは、LaunchPadを表示させるときに設定するキーです。ほかにも、"vk\_mission\_control"とか、"vk\_dashboard"といったキーが用意されています。どんなキーが用意されているかは、設定画面の「Simple Modifications」の「To Key」に表示されるキーで確認できます。

```
{
  "description": "control-EscでLaunchPad表示",
  "manipulators": [
    {
      "type": "basic",
      "from": {
        "key_code": "escape",
        "modifiers": { "mandatory": [ "control" ] }
      },
      "to": [
        { "key_code": "vk_launchpad" }
      ]
    }
  ]
}
```

## [](https://qiita.com/s-show/items/40ad22c4ee4a0465fad5#f5%E3%82%84escape%E7%AD%89%E3%81%AE%E5%8D%98%E7%8B%AC%E3%81%AE%E3%82%AD%E3%83%BC%E3%82%92control-o%E3%81%AE%E3%82%88%E3%81%86%E3%81%AA%E7%B5%84%E3%81%BF%E5%90%88%E3%82%8F%E3%81%9B%E3%81%AB%E5%A4%89%E6%8F%9B)"F5"や"Escape"等の単独のキーを"control-O"のような組み合わせに変換

この設定を行う場合、`"from"`の`"key_code"`に変換したいキーを設定すればOKです。もし、capslockのON・OFFに関わらず変換を実施したい場合、`"optional"`に"caps\_lock"または"any"を設定します。

```
{
  "description": "Browser（F5 -> command-r）",
  "manipulators": [
    {
      "type": "basic",
      "from": { "key_code": "f5" },
            "modifiers": { "optional": [ "caps_lock", "fn" ] },
      "to": [
        {
          "key_code": "r",
          "modifiers": [ "command" ]
        }
      ]
    }
  ]
}
```

~/\* capslockがONの状態でF5キーを押すと、なぜか"F5 + capslock + FN"キーの組み合わせになってしまうため、`"optional"`には`caps_lock`と`fn`を指定しています。~

本記事執筆当時は上記のような不具合がありましたが、現在（2018年12月10日時点）ではcapslockがONの状態で"F5"を押しても、"F5"のみ押されたことになりますので、`"optional"`の設定は不要かもしれません。

## [](https://qiita.com/s-show/items/40ad22c4ee4a0465fad5#%E7%89%B9%E5%AE%9A%E3%81%AE%E3%82%AD%E3%83%BC%E3%82%92%E7%84%A1%E5%8A%B9%E5%8C%96%E3%81%99%E3%82%8B)特定のキーを無効化する

特定のキーを無効化する処理は、`"to"`を省略することで実現できます。

なお、この設定を行う際は、どのアプリでも無効化したいキーでない限り、`"conditions/bundle_identifiers"`オプションでアプリを限定した方が良いと思います。`"conditions/bundle_identifiers"`オプションの使い方は、下の「特定のアプリでのみ（またはその反対）変換を実行する」を読んでください。

```
{
  "description": "control-Aの無効化（CotEditor限定）",
  "manipulators": [
    {
      "type": "basic",
      "from": {
        "key_code": "a",
        "modifiers": {
          "mandatory": ["control"]
        }
      },
      "conditions": [
        {
          "type": "frontmost_application_if",
          "bundle_identifiers": ["com\\.coteditor\\.CotEditor$"]
        }
      ]
    }
  ]
}
```

## [](https://qiita.com/s-show/items/40ad22c4ee4a0465fad5#%E4%BB%BB%E6%84%8F%E3%81%AE%E3%82%AD%E3%83%BC%E3%81%AB%E3%83%9E%E3%82%A6%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%83%E3%82%AF%E3%82%92%E5%89%B2%E3%82%8A%E5%BD%93%E3%81%A6%E3%82%8B)任意のキーにマウスクリックを割り当てる

マウスクリックを割り当てる場合、`"key_code"`の代わりに`"pointing_button"`を指定します。左右クリックとホイールクリックは次の通り指定します。

-   左クリック -> "button1"
-   右クリック -> "button2"
-   ホイールクリック -> "middle"

Karabiner-EventViewerで`"pointing_button"`に設定するマウスクリックの名称を調査できますので、左右クリックとホイールクリック以外を設定する場合、自分で調べて設定してください。  
また、以下のように `"optional"`に"any"を設定すると、"shift"や"command"等のキーを押しながら"Application"を押した場合に、それらのキーを押しながら右クリックしたのと同じ動作が実現できます。

```
{
    "description": "Applicationキーで右クリック",
    "manipulators": [
        {
            "type": "basic",
            "from": {
                "key_code": "application",
                "modifiers": { "optional": [ "any" ] }
            },
            "to": [
                { "pointing_button": "button2" }
            ]
        }
    ]
}
{
    "description": "shift-F10で右クリック",
    "manipulators": [
        {
            "type": "basic",
            "from": {
                "key_code": "f10",
                "modifiers": { "mandatory": [ "shift" ] }
            },
            "to": [
                { "pointing_button": "button2" }
            ]
        }
    ]
}
```

## [](https://qiita.com/s-show/items/40ad22c4ee4a0465fad5#%E4%BB%BB%E6%84%8F%E3%81%AE%E3%82%AD%E3%83%BC%E3%81%AB%E3%82%B3%E3%83%9E%E3%83%B3%E3%83%89%E5%AE%9F%E8%A1%8C%E3%82%92%E5%89%B2%E3%82%8A%E5%BD%93%E3%81%A6%E3%82%8B)任意のキーにコマンド実行を割り当てる。

この設定を行う場合、`"to"`の`"shell_command"`に実行したいコマンド文字列を設定します。コマンド文字列は、基本的にターミナルで打ち込むコマンドを""で囲んだ文字列になりますが、引数は""で囲む必要があります。  
（例："shell\_command": "open -a "iTunes.app""）

`"shell_command"`に設定できるコマンドの長さは、バージョン12.2.0までは256bytedでしたが、12.2.0から32KBまで拡張されました。

```
{
  "description": "command-EでFinderを開く",
  "manipulators": [
    {
      "type": "basic",
      "from": {
        "key_code": "e",
        "modifiers": {
          "mandatory": [ "command" ],
          "optional": [ "any" ]
        }
      },
      "to": [
        { "shell_command": "open -a "finder"" }
      ]
    }
  ]
}
```

## [](https://qiita.com/s-show/items/40ad22c4ee4a0465fad5#%E4%B8%80%E5%9B%9E%E3%81%AE%E3%82%AD%E3%83%BC%E3%82%BF%E3%82%A4%E3%83%97%E3%81%A7%E8%A4%87%E6%95%B0%E5%9B%9E%E3%81%AE%E3%82%AD%E3%83%BC%E3%82%BF%E3%82%A4%E3%83%97%E3%82%92%E5%AE%9F%E7%8F%BE%E3%81%99%E3%82%8B)一回のキータイプで複数回のキータイプを実現する

この変換を実現したい場合、`"to"`の値に複数の`"key_code"`を設定すればOKです。  
以下の設定例は、"Escape"を一度押すと、"Escape"を押した後に"japanese\_eisuu（英数）"をタイプしたことにする設定です。

```
{
    "description": "ESCを押したら強制的にIMEをオフにする",
    "manipulators": [
        {
            "type": "basic",
            "from": {
                "key_code": "escape"
            },
            "to": [
                { "key_code": "escape" },
                { "key_code": "japanese_eisuu" }
            ]
        }
    ]
}
```

## [](https://qiita.com/s-show/items/40ad22c4ee4a0465fad5#%E5%8D%98%E7%8B%AC%E3%81%A7%E6%8A%BC%E3%81%97%E3%81%9F%E5%A0%B4%E5%90%88%E3%81%A8%E7%B5%84%E3%81%BF%E5%90%88%E3%82%8F%E3%81%9B%E3%81%A7%E6%8A%BC%E3%81%97%E3%81%9F%E5%A0%B4%E5%90%88%E3%81%A7%E9%81%95%E3%81%86%E5%A4%89%E6%8F%9B%E3%82%92%E8%A1%8C%E3%81%86)単独で押した場合と組み合わせで押した場合で違う変換を行う

この設定を行う場合、単独で押した場合と組み合わせで押した場合の挙動をそれぞれ設定する必要があります。

方法は2つあり、1つ目の方法は、`"to_if_alone"`に単独で押した場合の挙動を設定し、`"to"`に組み合わせで押した場合の挙動を設定するという方法です。"control"や"command"キー等について、単独で押した場合に特別な動作を割り当て、他のキーと組み合わせて押した場合は"control"や"command"キーとして使う、という設定が考えられます。

2つ目の方法は、1つの`"description"`に2つの変換ルールを設定してまとめて適用するという方法です。私が設定しているのは、"capslock"キーについて、Windowsのように、単独で押した場合は"英数"キーとして、"shift"キーと組み合わせた場合は大文字・小文字入力の切り替えを行う"capslock"キーとして使うというものです。  
←  
それぞれの方法を紹介しますが、1つ目の方法は、`"from"`に設定するキーは1種類で、それを`"to"`と`"to_if_alone"`の2種類の動作に振り分ける形です。一方、2つ目の方法は、`"from"`と`"to"`の組み合わせを2種類用意することになります。目的にあった方を使ってください。

### [](https://qiita.com/s-show/items/40ad22c4ee4a0465fad5#%E6%96%B9%E6%B3%951)方法1

```
{
  "description": "commandキー単体で押したら英数・かなキーに変換。組み合わせで押したらcommandキーとして使う。",
  "manipulators": [
    {
      "type": "basic",
      "from": {
        "key_code": "left_command",
        "modifiers": { "optional": [ "any" ] }
      },
      "to": [
        {
          "key_code": "left_command",
          "lazy": true
        }
      ],
      "to_if_alone": [
        { "key_code": "japanese_eisuu" }
      ]
    },
    {
      "type": "basic",
      "from": {
        "key_code": "right_command",
        "modifiers": { "optional": [ "any" ] }
      },
      "to": [
        {
          "key_code": "right_command",
          "lazy": true
        }
      ],
      "to_if_alone": [
        { "key_code": "japanese_kana" }
      ]
    }
  ]
}
```

### [](https://qiita.com/s-show/items/40ad22c4ee4a0465fad5#%E6%96%B9%E6%B3%952)方法2

注意点として、以下のように1つの`"description"`の中に2つ以上の`"type"`を作ったのに期待した動作にならない場合、`"type"`の順番を入れ替えると期待通りに動作することがあります。

```
{
  "description": "capslock単体なら英数キー、shift-capslockならcapslockのON/OFF切り替え",
  "manipulators": [
    {
      "type": "basic",
      "from": {
        "key_code": "caps_lock",
        "modifiers": { "mandatory": [ "shift" ], "optional": [ "caps_lock" ] }
      },
      "to": [
        { "key_code": "caps_lock" }
      ]
    },
    {
      "type": "basic",
      "from": {
        "key_code": "caps_lock",
        "modifiers": { "optional": [ "any" ] }
      },
      "to": [
        { "key_code": "japanese_eisuu" }
      ]
    }
  ]
}
```

## [](https://qiita.com/s-show/items/40ad22c4ee4a0465fad5#a%E3%82%92%E6%8A%BC%E3%81%97%E3%81%AA%E3%81%8C%E3%82%89b%E3%82%92%E6%8A%BC%E3%81%97%E3%81%9F%E3%82%89c%E3%81%AB%E5%A4%89%E6%8F%9B%E3%81%99%E3%82%8B)"A"を押しながら"B"を押したら"C"に変換する

\---2017年11月19日全面書き換え---

`"modifiers"`には"A"や"D"等のキーも設定できますので、例えば、"A"を押しながら"B"を押すと"左カーソル"に変換するという設定も可能です。具体的には、次のようコードになります。

```
{
  "type": "basic",
  "from": {
    "key_code": "b",
    "modifiers": { "mandatory": [ "a" ] }
  },
  "to": [
    { "key_code": "left_arrow" }
  ]
}
```

しかし、上記の設定では、"A"を押してから"B"を押すまでの間、"A"が入力され続けてしまいます。  
`"modifiers"`に"command, shift, control, option, caps\_lock, fn"キーを設定した場合、設定した（例えば"fn"）を押すと`FlagsChanged`イベントが発生して次のキー入力（"fn-A"の"A"の部分）を待ちます。

しかし、"A"や"D"等を指定した場合、`FlagsChanged`イベントが発生せず、そのキーが押されている状態になります。そのため、「"A"を押してから"B"を押すまでの間、"A"が入力され続ける」という動作になります。

2018年12月9日追記

上記の設定を実際に使った場合、ログに次のエラーが記録されますので、今後のバージョンアップで上記のような"A"キーを`"modifiers"`に指定することはできなくなるかもしれません。

```
"complex_modifications json error: Unknown modifier: a"
```

## [](https://qiita.com/s-show/items/40ad22c4ee4a0465fad5#%E3%81%82%E3%82%8B%E3%82%AD%E3%83%BC%E3%82%92%E6%8A%BC%E3%81%97%E3%81%A6%E3%81%84%E3%82%8B%E9%96%93%E3%81%AF%E4%BB%96%E3%81%AE%E3%82%AD%E3%83%BC%E3%81%AE%E5%8B%95%E4%BD%9C%E3%82%92%E5%A4%89%E6%9B%B4%E3%81%99%E3%82%8B)あるキーを押している間は他のキーの動作を変更する

\---2018年12月10日全面書き換え---

この動作を実現させるには、次の2つの方法があります。

1.  `"set_variable"`を使う方法
2.  トリガーとなる最初のキー（上記設定の"A"に相当）を"fn"に変換する方法

### [](https://qiita.com/s-show/items/40ad22c4ee4a0465fad5#set_variable%E3%82%92%E4%BD%BF%E3%81%86%E6%96%B9%E6%B3%95)`"set_variable"`を使う方法

`"set_variable"`を使って、最初のキーを押した時点でフラグを立て、フラグが立っている間に次のキーを押すと指定した処理を行い、最初のキーから手を離したらフラグを下ろす、という処理方法です。

-   "PrintScreen"を押したら`"set_variable"`で`"printscreen_key"`変数に1を代入
-   "PrintScreen"から手を離したら`"printscreen_key"`の値を0にする
-   "P"を押した時に`"printscreen_key"`変数の値が1ならスクリーンショット撮影とプレビューアプリでの表示を行う
-   "P"を押した時に`"printscreen_key"`の値が1以外なら通常どおり"P"を押したことにする
-   PrintScreenを押した後、他のキーを押さずに手を離したらスクリーンショットの撮影を行う。

```
{
  "type": "basic",
  "from": { "key_code": "print_screen" },
  "to": [
    { "set_variable": { "name": "printscreen_key", "value": 1 } }
  ],
  "to_if_alone": [
    { "shell_command": "screencapture ~/Desktop/screenshot-`date +%Y%m%d-%H%M%S`.png" }
  ],
  "to_after_key_up": [
    { "set_variable": { "name": "printscreen_key", "value": 0 } }
  ],
  "conditions": [
    { "type": "variable_if", "name": "printscreen_key", "value": 0 }
  ]
},
{
  "type": "basic",
  "from": { "key_code": "p" },
  "to": [
    { "shell_command": "screencapture -P ~/Desktop/screenshot-`date +%Y%m%d-%H%M%S`.png" }
  ],
  "conditions": [
    { "type": "variable_if", "name": "printscreen_key", "value": 1 }
  ]
}
```

### [](https://qiita.com/s-show/items/40ad22c4ee4a0465fad5#%E6%9C%80%E5%88%9D%E3%81%AE%E3%82%AD%E3%83%BC%E3%82%92fn%E3%81%AB%E5%A4%89%E6%8F%9B%E3%81%99%E3%82%8B%E6%96%B9%E6%B3%95)最初のキーを"fn"に変換する方法

こちらの方法は変数管理が不要になる分、上記の方法より楽に設定できます。

最初のキーを"fn"に変換する設定を行い、次のキーについては、`"modifiers"`の`"mandatory"`に"fn"を指定して、"fn"と一緒に押さないと変換されないように設定します。"fn"に変換する理由は、"shift"や"command"とは異なり、既存のショートカットキーとの衝突が避けられるためです。

```
{
  "type": "basic",
  "from": { "key_code": "print_screen" },
  "to": [
    { "key_code": "fn" }
  ],
  "to_if_alone": [
    { "shell_command": "screencapture ~/Desktop/screenshot-`date +%Y%m%d-%H%M%S`.png" }
  ]
},
{
  "type": "basic",
  "from": {
    "key_code": "p",
    "modifiers": { "mandatory": [ "fn" ] }
  },
  "to": [
    { "shell_command": "screencapture -P ~/Desktop/screenshot-`date +%Y%m%d-%H%M%S`.png" }
  ]
}
```

この方法を応用すると、JISキーボードでほとんど使わない"無変換"キーを"fn"キー代わりに使い、"無変換"キーと別のキーの組み合わせに色々な処理を割り当てることができます。

以下の例は、"無変換/英数"を押している間だけ、"スペースキー"を"Enterキー"に変換する設定です。\[Karabiner-Elementsでenthumble（Windows App）のような操作を実現する方法 - Qiita\]（[https://qiita.com/s-show/items/0036e45d4b5928569dd9）で紹介している方法は、この方法で実現しています。](https://qiita.com/s-show/items/0036e45d4b5928569dd9%EF%BC%89%E3%81%A7%E7%B4%B9%E4%BB%8B%E3%81%97%E3%81%A6%E3%81%84%E3%82%8B%E6%96%B9%E6%B3%95%E3%81%AF%E3%80%81%E3%81%93%E3%81%AE%E6%96%B9%E6%B3%95%E3%81%A7%E5%AE%9F%E7%8F%BE%E3%81%97%E3%81%A6%E3%81%84%E3%81%BE%E3%81%99%E3%80%82)

```
{
  "description": "無変換/英数 + 「スペース/かな」で「Return/Escape」",
  "manipulators": [
    {
      "type": "basic",
      "from": {
        "key_code": "spacebar",
        "modifiers": {
          "mandatory": [ "fn" ],
          "optional": [ "shift", "control", "caps_lock" ]
        }
      },
      "to": [
        { "key_code": "return_or_enter" }
      ]
    },
    {
      "type": "basic",
      "from": {
        "key_code": "international5",
        "modifiers": {
          "optional": [ "caps_lock" ]
        }
      },
      "to": [
        { "key_code": "fn" }
      ],
      "to_if_alone": [
        { "key_code": "japanese_eisuu" }
      ]
    }
  ]
}
```

## [](https://qiita.com/s-show/items/40ad22c4ee4a0465fad5#%E3%82%AD%E3%83%BC%E3%81%AE2%E9%80%A3%E6%89%93%E3%81%AB%E7%89%B9%E5%AE%9A%E3%81%AE%E5%87%A6%E7%90%86%E3%82%92%E5%89%B2%E3%82%8A%E5%BD%93%E3%81%A6%E3%82%8B)キーの2連打に特定の処理を割り当てる

\---2017年11月19日新規追加---

次のような設定で実現します。

1.  最初のキー（shift等）を押したら`"set_variable"`を使って変数に1を代入（フラグを立てる）
2.  次に同じキーを押した時に変数の値が1なら（フラグが立っている）、実行したい処理を行うよう設定する。

### [](https://qiita.com/s-show/items/40ad22c4ee4a0465fad5#%E5%B7%A6control2%E9%80%A3%E6%89%93%E3%81%A7safari%E3%82%92%E8%B5%B7%E5%8B%95)左control2連打でSafariを起動

ポイントは、2つ目の`"type"`の`"to"`で、変数に値を格納した後、`"key_code": "left_control"`を指定していることです。この設定を省略すると、左controlを左controlとして使うことができなくなります。端的に言うと、左controlを使って"ctrl-A"のようなショートカットキーを使うことができなくなります。

また、`"to_delayed_action"`の`"to_if_invoked"`と`"to_if_canceled"`を設定して、最初のキーを押してから一定の時間が経過した時と、最初のキーと違うキーを押した場合に`left_control_key`変数の値を初期化する設定も行う必要があります。  
なお、`"from"`に"control"と入力しても、左右のcontrolをまとめて設定することはできません。左右のcontrolに同じ設定をしたい場合、それぞれのキーについて設定を行う必要があります。

```
{
  "description": "左controlを2回連打したらSafariを起動する",
  "manipulators": [
    {
      "type": "basic",
      "from": { "key_code": "left_control" },
      "to": [
        { "shell_command": "open -a "safari"" }
      ],
      "conditions": [
        { "type": "variable_if", "name": "left_control_key", "value": 1 }
      ]
    },
    {
      "type": "basic",
      "from": {
        "key_code": "left_control",
        "modifiers": { "optional": [ "any" ] }
      },
      "to": [
        { "set_variable": { "name": "left_control_key", "value": 1 } },
        { "key_code": "left_control" }
      ],
      "to_delayed_action": {
        "to_if_invoked": [
          { "set_variable": { "name": "left_control_key", "value": 0 } }
        ],
        "to_if_canceled": [
          { "set_variable": { "name": "left_control_key", "value": 0 } }
        ]
      },
      "conditions": [
        { "type": "variable_if", "name": "left_control_key", "value": 0 }
      ]
    }
  ]
}
```

### [](https://qiita.com/s-show/items/40ad22c4ee4a0465fad5#%E3%83%86%E3%83%B3%E3%82%AD%E3%83%BC%E3%81%AE%E3%83%94%E3%83%AA%E3%82%AA%E3%83%892%E9%80%A3%E6%89%93%E3%82%92%E3%82%AB%E3%83%B3%E3%83%9E%E3%81%AB%E5%A4%89%E6%8F%9B)テンキーのピリオド2連打をカンマに変換

実装方法は、上記の左controlとほぼ同じですが、1つ工夫したところがあります。

それは、1回目のピリオド入力の時点で、変数に1を代入してフラグを立てた後、一度"."を入力し、次にピリオドを入力したら、入力済みのピリオドを削除してからコンマを入力するようにしたことです。

これにより、"1.0"のような入力をする際に、タイプした通りに画面に入力した内容を表示することができるようになりました。

```
{
  "description": "テンキーの".（ピリオド）"2連打で",（カンマ）"を入力",
  "manipulators": [
    {
      "type": "basic",
      "from": { "key_code": "keypad_period" },
      "to": [
        # 以下の {"key_code": "keypad_period"} で入力された"."を削除する
        { "key_code": "delete_or_backspace" },
        { "key_code": "comma" },
        { "set_variable": { "name": "press_period_key", "value": 0 } }
      ],
      "conditions": [
        { "type": "variable_if", "name": "press_period_key", "value": 1 }
      ]
    },
    {
      "type": "basic",
      "from": { "key_code": "keypad_period" },
      "to": [
        { "set_variable": { "name": "press_period_key", "value": 1 } },
        { "key_code": "keypad_period" }
      ],
      "to_delayed_action": {
        "to_if_invoked": [
          { "set_variable": { "name": "press_period_key", "value": 0 } }
        ],
        "to_if_canceled": [
          { "set_variable": { "name": "press_period_key", "value": 0 } }
        ]
      },
      "conditions": [
        { "type": "variable_if", "name": "press_period_key", "value": 0 }
      ]
    }
  ]
}
```

## [](https://qiita.com/s-show/items/40ad22c4ee4a0465fad5#emacs%E3%81%AEcontrol-x-control-f%E3%81%AE%E3%82%88%E3%81%86%E3%81%AA2%E6%AE%B5%E9%9A%8E%E3%81%AE%E3%82%AD%E3%83%BC%E3%82%B9%E3%83%88%E3%83%AD%E3%83%BC%E3%82%AF%E3%82%92%E5%AE%9F%E7%8F%BE%E3%81%99%E3%82%8B)Emacsの"control-x control-f"のような2段階のキーストロークを実現する

\---2017年11月17日全面書き換え---

Ver.11.1.12で追加された`to_delayed_action`, `to_if_invoked`, `to_if_canceled`という3つの設定項目を活用します。具体的な設定は以下のとおりです。

```
{
  "description": "Two stroke key_bind",
  "manipulators": [
    {
      "type": "basic",
      "from": {
        "key_code": "c",
        "modifiers": { "mandatory": [ "control" ] }
      },
      "to": [
        { 
            "key_code": "q",
            "modifiers": [ "command" ] 
        }
      ],
      "conditions": [
        { "type": "variable_if", "name": "ctrl-x", "value": 1 }
      ]
    },
    {
      "type": "basic",
      "from": {
        "key_code": "f",
        "modifiers": { "mandatory": [ "control" ] }
      },
      "to": [
        {
          "key_code": "o",
          "modifiers": [ "command" ]
         }
      ],
      "conditions": [
        { "type": "variable_if", "name": "ctrl-x", "value": 1 }
      ]
    },
    {
      "type": "basic",
      "from": {
        "key_code": "x",
        "modifiers":
         { "mandatory": [ "control" ], "optional": [ "caps_lock" ] }
      },
      "to": [
        { "set_variable": { "name": "ctrl-x", "value": 1 } }
      ],
      "to_if_alone": [
         { "key_code": "x" }
      ],
      "to_delayed_action": {
        "to_if_invoked": [
          { "set_variable": { "name": "ctrl-x", "value": 0 } }
        ],
        "to_if_canceled": [
          { "set_variable": { "name": "ctrl-x", "value": 0 } }
        ]
      },
      "conditions": [
        { "type": "variable_if", "name": "ctrl-x", "value": 0 }
      ]
    }
  ]
}
```

このコードは以下のとおり動作します。

1.  "control-x"を押すと`ctrl-x`変数に2を代入する（`to`の`set_variable`が実行される）
2.  次にタイプしたキーにより、以下の処理が行われる。
    1.  "control-c" -> "command-q"に変換
    2.  "control-f" -> "command-f"に変換
    3.  上記1〜2以外 -> `ctrl-x`変数に0を代入する。（`to_if_canceled`の`set_variable`が実行される）
3.  "control-x"をタイプした後、一定の時間が経過すると`ctrl-x`変数に0を代入する。（`to_if_invoked`の`set_variable`が実行される）

## [](https://qiita.com/s-show/items/40ad22c4ee4a0465fad5#%E7%89%B9%E5%AE%9A%E3%81%AE%E3%82%A2%E3%83%97%E3%83%AA%E3%81%A7%E3%81%AE%E3%81%BF%E3%81%BE%E3%81%9F%E3%81%AF%E3%81%9D%E3%81%AE%E5%8F%8D%E5%AF%BE%E5%A4%89%E6%8F%9B%E3%82%92%E5%AE%9F%E8%A1%8C%E3%81%99%E3%82%8B)特定のアプリでのみ（またはその反対）変換を実行する

特定のアプリでのみ変換を実行したい場合、`"conditions"`の`"type"`に`"frontmost_application_if"`を設定し、あわせて`"bundle_identifiers"`でアプリを指定します。以下の例は、Safariだけで変換を実行するため、`"^com\\.apple\\.Safari"`を指定しています。  
反対に、特定のアプリ以外で変換を実行したい場合、`"conditions"`の`"type"`に`"frontmost_application_unless"`を設定し、あわせて`"bundle_identifiers"`に変換を実行したくないアプリを指定します。

`"bundle_identifiers"`に指定するアプリの名前は、"Karabiner-EventViewer"を立ち上げてから指定したいアプリを一度選択し、また"Karabiner-EventViewer"を選択して"Frontmost Application"タブを開けば確認できます。

```
{
  "type": "basic",
  "from": {
    "key_code": "page_up",
    "modifiers": {
      "mandatory": [ "control" ]
    }
  },
  "to": [
    {
      "key_code": "tab",
      "modifiers": [ "control", "shift" ]
    }
  ],
  "conditions": [
    {
      "type": "frontmost_application_if",
      "bundle_identifiers": [ "^com\\.apple\\.Safari" ]
    }
  ]
}
```

## [](https://qiita.com/s-show/items/40ad22c4ee4a0465fad5#ime%E3%81%AE%E7%8A%B6%E6%85%8B%E3%81%AB%E5%BF%9C%E3%81%98%E3%81%A6%E5%87%A6%E7%90%86%E3%82%92%E5%A4%89%E3%81%88%E3%82%8B--ime%E3%81%AE%E7%8A%B6%E6%85%8B%E3%82%92%E5%88%87%E3%82%8A%E6%9B%BF%E3%81%88%E3%81%9F%E3%81%84)IMEの状態に応じて処理を変える & IMEの状態を切り替えたい

IMEの状態に応じて処理を変える場合、`"conditions"`の`"type"`に`"input_sources"`を設定し、`"language"`でIMEの状態を指定します。また、IMEの状態をKarabiner-Elementsで直接切り替える場合、`"to"`に`"select_input_source"`を設定し、`"input_source_id"`でIMEの状態をしています。`"input_sources"`や`"input_source_id"`に指定するIMEの状態については、"Karabiner-EventViewer"の"Variables"で確認できます。

なお、IMEの状態の切り替えについては、`"to"`に`"key_code": "japanese_eisuu"`または`"key_code": "japanese_kana"`を指定しても切り替えられます。これは、"英数"や"かな"を押してIMEを切り替えることと同じ動作を行うものです。

以下の設定は、Windowsのように、JISキーボードの"全角/半角"をIME切り替えキーとして使う設定です。ちなみに、Karabiner-Elementsでは、JISキーボードの"全角/半角"は"grave\_accent\_and\_tilde"と指定します。

```
{
  "description": "全角/半角でIMEのON/OFFを切り替える",
  "manipulators": [
    {
      "type": "basic",
      "from": { "key_code": "grave_accent_and_tilde" },
      "to": [
        {
          "select_input_source": {
            "input_source_id": "^com\\.apple\\.inputmethod\\.Kotoeri\\.Japanese$"
          }
        }
      ],
      "conditions": [
        {
          "type": "input_source_if",
          "input_sources": [
            { "language": "en" }
          ]
        }
      ]
    },
    {
      "type": "basic",
      "from": { "key_code": "grave_accent_and_tilde" },
      "to": [
        {
          "select_input_source": {
            "input_source_id": "^com\\.apple\\.inputmethod\\.Kotoeri\\.Roman$"
          }
        }
      ],
      "conditions": [
        {
          "type": "input_source_if",
          "input_sources": [
            { "language": "ja" }
          ]
        }
      ]
    }
  ]
}
```

## [](https://qiita.com/s-show/items/40ad22c4ee4a0465fad5#%E3%83%9E%E3%82%A6%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%83%E3%82%AF%E3%81%AB%E5%87%A6%E7%90%86%E3%82%92%E5%89%B2%E3%82%8A%E5%BD%93%E3%81%A6%E3%82%8B)マウスクリックに処理を割り当てる

`"from"`に`"key_code"`ではなく`"pointing_button"`を指定すると、マウスクリックに何らかの処理を割り当てることが可能になります。

ただし、`"pointing_button"`に"button1"を指定した場合、左クリックに何らかの処理を割り当てることになりますので、左クリックが左クリックとして使用できなくなります。この点には十分注意して設定を行う必要があります。  
なお、この処理はVer.11.2.0以降で可能となったようです。

```
{
  "description": "Finderでミドルクリックをしたら新しいタブで開く",
  "manipulators": [
    {
      "type": "basic",
      "from": { "pointing_button": "button3" },
      "to": [
        {
          "key_code": "t",
          "modifiers": [ "command" ]
        }
      ],
      "conditions": [
        {
          "type": "frontmost_application_if",
          "bundle_identifiers": [ "^com\\.apple\\.finder$" ]
        }
      ]
    }
  ]
}
```

## [](https://qiita.com/s-show/items/40ad22c4ee4a0465fad5#%E3%82%AD%E3%83%BC%E3%83%9C%E3%83%BC%E3%83%89%E3%81%A7%E3%83%9E%E3%82%A6%E3%82%B9%E6%93%8D%E4%BD%9C%E3%82%92%E5%AE%9F%E7%8F%BE%E3%81%99%E3%82%8B)キーボードでマウス操作を実現する

### [](https://qiita.com/s-show/items/40ad22c4ee4a0465fad5#%E3%83%9E%E3%82%A6%E3%82%B9%E3%82%AB%E3%83%BC%E3%82%BD%E3%83%AB%E3%81%AE%E7%A7%BB%E5%8B%95%E3%81%A8%E3%83%9B%E3%82%A4%E3%83%BC%E3%83%AB%E3%82%B9%E3%82%AF%E3%83%AD%E3%83%BC%E3%83%AB%E3%81%AE%E5%AE%9F%E7%8F%BE)マウスカーソルの移動とホイールスクロールの実現

キーボード操作でマウスカーソルやホイールスクロールの操作を行うことも可能です。

以下の設定例は、"右Shift-WSAD"でカーソルの上下左右の移動を、"右Shift-RV"で上下のホイールスクロールを実現させるというものです。

```
{
  "type": "basic",
  "from": {
    "key_code": "w",
    "modifiers": {
      "mandatory": [ "right_shift" ]
    }
  },
  "to": [
    { "mouse_key": { "y": -1536 } }
  ]
},
{
  "type": "basic",
  "from": {
    "key_code": "a",
    "modifiers": {
      "mandatory": [ "right_shift" ]
    }
  },
  "to": [
    { "mouse_key": { "x": -1536 } }
  ]
},
{
  "type": "basic",
  "from": {
    "key_code": "s",
    "modifiers": {
      "mandatory": [ "right_shift" ]
    }
  },
  "to": [
    { "mouse_key": { "y": 1536 } }
  ]
},
{
  "type": "basic",
  "from": {
    "key_code": "d",
    "modifiers": {
      "mandatory": [ "right_shift" ]
    }
  },
  "to": [
    { "mouse_key": { "x": 1536 } }
  ]
},
{
  "type": "basic",
  "from": {
    "key_code": "r",
    "modifiers": {
      "mandatory": [ "right_shift" ]
    }
  },
  "to": [
    { "mouse_key": { "vertical_wheel": -32 } }
  ]
},
{
  "type": "basic",
  "from": {
    "key_code": "v",
    "modifiers": {
      "mandatory": [ "right_shift" ]
    }
  },
  "to": [
    { "mouse_key": { "vertical_wheel": 32 } }
  ]
}
```

### [](https://qiita.com/s-show/items/40ad22c4ee4a0465fad5#%E3%83%80%E3%83%96%E3%83%AB%E3%82%AF%E3%83%AA%E3%83%83%E3%82%AF%E3%82%92%E5%AE%9F%E7%8F%BE%E3%81%99%E3%82%8B)ダブルクリックを実現する

以下のの設定のように`"to"`に`"pointing_button": "button1"`を2つ連続で設定するとダブルクリックを再現できるようです。

以下の設定は、Finderでファイルを選択してEnterを押すとWindowsと同様にファイルが開くようにするものです。

注意点は、マウスカーソルが他のファイルの上にあると、そちらのファイルの方が開かれてしまうということです。つまり、ファイルを選択しているという状態を無視して、その時のマウスカーソルがある場所でダブルクリックを行ったことになるということです。

```
{
  "type": "basic",
  "from": { "key_code": "return_or_enter" },
  "to": [
    { "pointing_button": "button1" },
    { "pointing_button": "button1" }
  ],
  "conditions": [
    {
      "type": "frontmost_application_if",
      "bundle_identifiers": [
        "^com\\.apple\\.finder$"
      ]
    }
  ]
}
```

## [](https://qiita.com/s-show/items/40ad22c4ee4a0465fad5#%E6%96%87%E5%AD%97%E5%85%A5%E5%8A%9B%E3%82%92%E5%AE%9F%E7%8F%BE%E3%81%99%E3%82%8B)文字入力を実現する

Karabiner-Elementsに文字入力の機能はありませんが、`"shell_command"`を使って次のような手順を実行すると、擬似的に文字入力を実現することができます。

1.  AppleScriptを実行して入力したい文字列をクリップボードに格納する
2.  AppleScriptのキー入力実現機能を使って貼り付けコマンド（command-V）を実行する

AppleScriptで、クリップボードに文字を格納して貼り付けするコマンドは次の通りですので、このコマンド文字列を`"shell_command"`に指定すれば文字入力が実現できます。なお、`"shell_command"`に指定するコマンド文字列は`"`で囲む必要がありますが、元のコマンド文字列に`"`が含まれている場合、`"`を`\`でエスケープ処理する必要があります。

```
# クリップボードに文字を格納
osascript -e "set the clipboard to "←""

# クリップボードのデータを貼り付け
osascript -e "tell application "System Events" to keystroke "v" using command down"
```

上記のコマンドを使って、"fn-左矢印"で"←"を入力するという設定は次のようになります。

```
{
  "description": ""fn-左矢印"で"←"入力",
  "manipulators": [
    {
      "type": "basic",
      "from": {
        "key_code": "left_arrow",
        "modifiers": {
          "mandatory": [ "fn" ],
          "optional": [ "caps_lock" ]
        }
      },
      "to": [
        { "shell_command": "osascript -e "set the clipboard to \"←\""" },
        {
          "shell_command": "osascript -e "tell application \"System Events\" to keystroke \"v\" using command down""
        }
      ]
    }
  ]
}
```

なお、上記の設定の注意点は、"fn-左矢印"を押してから"←"が入力されるまで、体感で0.5秒くらい待たされるということです。そのため、"fn-左矢印"を押してすぐ"A"とかを押すと、"A"が入力されてから"←"が入力されたりします。

AppleScriptの動作が早ければこういう問題も起きないのですが、現状では仕様と思ってあきらめるしかありません。

## [](https://qiita.com/s-show/items/40ad22c4ee4a0465fad5#2%E3%81%A4%E4%BB%A5%E4%B8%8A%E3%81%AE%E3%82%AD%E3%83%BC%E3%81%AE%E5%90%8C%E6%99%82%E6%8A%BC%E3%81%97%E3%81%AB%E5%87%A6%E7%90%86%E3%82%92%E5%89%B2%E3%82%8A%E5%BD%93%E3%81%A6%E3%82%8B)2つ以上のキーの同時押しに処理を割り当てる

2つ以上のキーの同時押しに処理を割り当てる場合、`"from"`の`"simultaneous"`に処理を割り当てたいキーを列挙します。

同時押しと判定される時間は、デフォルトでは50ミリ秒です。以下の設定は、"S, D, F"を同時に押すとランチャーアプリの"Alfred"が起動するというものですが、厳密に"S, D, F"を同時に押さなくても、50ミリ秒以内に"S → D →F"の順番で押しても"Alfred"が起動します。

もし、同時押しと認識される時間を変更したい場合、設定画面の「Complex Modifications / Parameters / simultaneous\_threshold\_milliseconds」に設定されている時間を変更します。

なお、同時押しはオプションが多い設定項目です。オプションを1つずつ紹介すると結構なボリュームになりますので、詳細は、[私が書いた記事](https://qiita.com/s-show/items/a1fd228b04801477729c#fromsimultaneoussimultaneous_options)で確認してください。

```
{
  "description": "S,D,Fの同時押しでAlfred起動",
  "manipulators": [
    {
      "type": "basic",
      "from": {
        "simultaneous": [
          { "key_code": "s" },
          { "key_code": "d" },
          { "key_code": "f" }
        ],
        "modifiers": {
          "optional": [ "any" ]
        }
      },
      "to": [
        { "shell_command": "open -a 'Alfred 3.app'" }
      ]
    }
  ]
}
```

## [](https://qiita.com/s-show/items/40ad22c4ee4a0465fad5#%E3%82%AD%E3%83%BC%E3%81%AE%E9%95%B7%E6%8A%BC%E3%81%97%E3%81%AB%E5%87%A6%E7%90%86%E3%82%92%E5%89%B2%E3%82%8A%E5%BD%93%E3%81%A6%E3%82%8B)キーの長押しに処理を割り当てる

キーの長押しに処理を割り当てる場合、長押しということで`"from"`側に設定すると思われるかもしれませんが、`"to_if_held_down"`に割り当てたい処理を記述します。

長押しと判定されるまでの時間は、デフォルトで500ミリ秒です。もし、長押しと判定されるまでの時間を変更したい場合は、`"parameters"`の`"basic.to_if_held_down_threshold_milliseconds"`に設定すれば、設定毎に時間を指定できます。

この設定を行う場合の注意点は、実行したい処理は1回だけ実行すれば良いのか、それとも連続して実行させる必要があるのかを決めておく必要があります。

例えば、次の設定はcommand-Qを1秒間押し続けないとcommand-Qが実行されないという設定です。この設定で`"repeat"`に`false`を設定していない場合、command-Qを1秒間長押ししてから手を離すまで、command-Qが連続して実行されてアプリがどんどん終了します。そうした事態を避けるため、`"repeat"`に`false`を指定して、処理の実行を1回に限定しています。

```
{
  "description": "１秒間押し続けないとcommand-qが実行されない設定",
  "manipulators": [
    {
      "type": "basic",
      "from": {
        "key_code": "q",
        "modifiers": { "mandatory": [ "command" ], "optional": [ "caps_lock" ] }
      },
      "parameters": { "basic.to_if_held_down_threshold_milliseconds": 1000 },
      "to_if_held_down": [
        { 
          "key_code": "q",
          "modifiers": [ "command" ],
          "repeat": false
        }
      ]
    }
  ]
}
```

## [](https://qiita.com/s-show/items/40ad22c4ee4a0465fad5#%E8%A3%9C%E8%B6%B3)補足

最後になりましたが、私の設定を公開していますので、よろしければ参考にしてください。  
\[s-show/KE-complex\_modifications\]（[https://github.com/s-show/KE-complex\_modifications/）](https://github.com/s-show/KE-complex_modifications/%EF%BC%89)

また、こちらのページから、私の設定をKarabiner-Elementsにimportできます。  
\[Karabiner-Elements complex\_modifications rules by s-show\]（[https://s-show.github.io/KE-complex\_modifications/）](https://s-show.github.io/KE-complex_modifications/%EF%BC%89)

なお、\[pqrs-org/KE-complex\_modifications\]（[https://github.com/pqrs-org/KE-complex\_modifications）で配布されているツールを使いますと、Karabiner-Elementsの設定ファイルを書くのが楽になります。](https://github.com/pqrs-org/KE-complex_modifications%EF%BC%89%E3%81%A7%E9%85%8D%E5%B8%83%E3%81%95%E3%82%8C%E3%81%A6%E3%81%84%E3%82%8B%E3%83%84%E3%83%BC%E3%83%AB%E3%82%92%E4%BD%BF%E3%81%84%E3%81%BE%E3%81%99%E3%81%A8%E3%80%81Karabiner-Elements%E3%81%AE%E8%A8%AD%E5%AE%9A%E3%83%95%E3%82%A1%E3%82%A4%E3%83%AB%E3%82%92%E6%9B%B8%E3%81%8F%E3%81%AE%E3%81%8C%E6%A5%BD%E3%81%AB%E3%81%AA%E3%82%8A%E3%81%BE%E3%81%99%E3%80%82)  
このツールの使い方については、\[KE-complex\_modificationsを使ってKarabiner-Elementsの定義を色々作って公開する\]（  
[https://rcmdnk.com/blog/2017/08/30/computer-mac-karabiner/）で詳しく解説されています。私も\[KE-complex\_modificationsを使ってKarabiner-Elementsの設定を楽にする方法](https://rcmdnk.com/blog/2017/08/30/computer-mac-karabiner/%EF%BC%89%E3%81%A7%E8%A9%B3%E3%81%97%E3%81%8F%E8%A7%A3%E8%AA%AC%E3%81%95%E3%82%8C%E3%81%A6%E3%81%84%E3%81%BE%E3%81%99%E3%80%82%E7%A7%81%E3%82%82%5BKE-complex_modifications%E3%82%92%E4%BD%BF%E3%81%A3%E3%81%A6Karabiner-Elements%E3%81%AE%E8%A8%AD%E5%AE%9A%E3%82%92%E6%A5%BD%E3%81%AB%E3%81%99%E3%82%8B%E6%96%B9%E6%B3%95) - Qiita\]（[https://qiita.com/s-show/items/fb788d90faba7eeb9051）という記事を書いていますので、参考にしてください。前者の記事では、Karabiner-Elementsの設定で役に立つ情報が色々ありますので、非常に参考になると思います。](https://qiita.com/s-show/items/fb788d90faba7eeb9051%EF%BC%89%E3%81%A8%E3%81%84%E3%81%86%E8%A8%98%E4%BA%8B%E3%82%92%E6%9B%B8%E3%81%84%E3%81%A6%E3%81%84%E3%81%BE%E3%81%99%E3%81%AE%E3%81%A7%E3%80%81%E5%8F%82%E8%80%83%E3%81%AB%E3%81%97%E3%81%A6%E3%81%8F%E3%81%A0%E3%81%95%E3%81%84%E3%80%82%E5%89%8D%E8%80%85%E3%81%AE%E8%A8%98%E4%BA%8B%E3%81%A7%E3%81%AF%E3%80%81Karabiner-Elements%E3%81%AE%E8%A8%AD%E5%AE%9A%E3%81%A7%E5%BD%B9%E3%81%AB%E7%AB%8B%E3%81%A4%E6%83%85%E5%A0%B1%E3%81%8C%E8%89%B2%E3%80%85%E3%81%82%E3%82%8A%E3%81%BE%E3%81%99%E3%81%AE%E3%81%A7%E3%80%81%E9%9D%9E%E5%B8%B8%E3%81%AB%E5%8F%82%E8%80%83%E3%81%AB%E3%81%AA%E3%82%8B%E3%81%A8%E6%80%9D%E3%81%84%E3%81%BE%E3%81%99%E3%80%82)
