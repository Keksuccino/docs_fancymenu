---
title: レイアウトの一部を切り替える
description: ユーザー入力に応じてレイアウトの一部を切り替える方法。
---

# レイアウトの一部を切り替える

ときには選択肢があると便利です！ たとえば、ユーザーの中にはメニュー音楽として Rick Astley が常に流れるのを好まない人や、メニュー背景として別のかわいいアニメの女の子を使いたい人もいるかもしれません。

もちろん問題ありません！ レイアウトの一部をオン/オフできるようにしたり、複数のバージョンを順番に切り替えたりできます。

# オン/オフを切り替える

たとえばボタンをクリックして要素の表示/非表示を切り替えるには、ボタンクリックで値が設定される変数を使い、切り替えたい要素側で読み込み条件としてその変数が正しい値かどうかを確認するようにします。

## 変数

最初に、切り替えたい要素の表示状態を保存するための変数を作成します。

新しい変数を追加するには、メニューバーの **Customization** タブに移動して **Variables -> Manage Variables** をクリックし、**一意** の名前で新しい変数を追加します。すでに使われていない、しっかり **一意** の名前を使ってください。

変数を作成したら、値を `true` に設定します。

<br>
<img width="494" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/1e29be13-e601-4669-8fa2-d78db945b07f">

## 要素

次のステップは、オン/オフを切り替えたい要素を追加することです。

<br>
<img width="270" alt="Screenshot_3" src="https://gist.github.com/assets/35544624/317460fc-310b-4941-ab9a-b56490c5ebb9">

次に、その要素を右クリックして **Loading Requirements** をクリックします。
すると Manage Requirements 画面が開きます。そこで **Add Requirement** をクリックします。

**Is Variable Value** 要件を検索して選択し、**Edit Requirement Value** をクリックします。

<br>
<img width="501" alt="Screenshot_1" src="https://gist.github.com/assets/35544624/d0d342f5-617c-415e-b6f7-05087fc204b7">

ここで、先ほど作成した変数名を入力し、要件が値として `true` を確認するようにします。

<br>
<img width="500" alt="Screenshot_2" src="https://gist.github.com/assets/35544624/a1f356e9-7f96-4d8b-87b0-51f05898409a">

これでこの部分は完了です。これで、変数の値が `true` のときに要素が表示されるようになります。

## ボタン

次に、新しい Button 要素を追加します。

<br>
<img width="270" alt="Screenshot_4" src="https://gist.github.com/assets/35544624/1bd1b781-0cdb-4b52-80a0-db8f44ead0db">

追加したら、それを右クリックして **Edit Action Script** をクリックします。
これでボタンの Manage Action Script 画面が開きます。

**Add IF Statement** をクリックし、そこに **Is Variable Value** 要件を追加して、要件のモードを **OPPOSITE** に設定します。

<br>
<img width="520" alt="Screenshot_5" src="https://gist.github.com/assets/35544624/a024ea21-2244-4ca6-b44b-1a80f7936b8f">

次に、要素で行ったのと同じように **Edit Requirement Value** をクリックし、同じ変数名と確認する値をそのまま入力します。

<br>
<img width="500" alt="Screenshot_2" src="https://gist.github.com/assets/35544624/a1f356e9-7f96-4d8b-87b0-51f05898409a">

要件のモードを **OPPOSITE** にしたので、これで変数の値が `true` **ではない** 場合を確認するようになります。これはまさに求めている動作です。

Edit Action Script 画面に戻ると、先ほど追加した IF ステートメントが表示されているはずです。

<br>
<img width="495" alt="Screenshot_6" src="https://gist.github.com/assets/35544624/6ac8444c-ca15-43ff-a633-df63e76e7433">

次に **Add Action** をクリックし、**Set Variable Value** アクションを検索して選択し、**Edit Action Value** をクリックします。

<br>
<img width="494" alt="Screenshot_7" src="https://gist.github.com/assets/35544624/8568e539-b4d0-49bd-89c4-4659ee71754c">

アクション値として、まず変数名、その後に設定したい値を入力します。名前と値は `:` で区切ってください。
この場合は、値を `true` に設定したいので、これは後で値が `true` **ではない** ときに実行されます。

<br>
<img width="496" alt="Screenshot_8" src="https://gist.github.com/assets/35544624/fab440ad-b335-4751-9651-4bb0b65bc968">

次に、そのアクションを IF ステートメントの上までドラッグして移動し、IF ステートメントに追加します。これで、変数の値が `true` ではない場合にのみ実行されるようになります。

<br>
<img width="496" alt="Screenshot_8" src="https://gist.github.com/assets/35544624/d1ac3ea9-44d7-4ad6-a4b2-455b21f6d1c4">

それが終わったら、IF ステートメントを選択して **Append ELSE Statement** をクリックします。

次に、もう1つ **Set Variable Value** アクションを追加します。ただし、変数の値を `true` にするのではなく、`false` に設定します。

<br>
<img width="494" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/d05400dc-b9b7-4c1a-8657-9e34939ed599">

今度は、2つ目のアクションを ELSE ステートメントに追加して、変数の値が `true` の場合に実行されるようにします。

<br>
<img width="494" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/3191a1cc-c5c2-4cf1-a620-23bdbe639bf2">

これで完了です！ 最初は手順が多く感じるかもしれませんが、慣れてしまえば実際にはかなり簡単で素早くできます。

これでレイアウトを保存し、エディタを終了して、ボタンを押して動作するか確認しましょう！

<br>
<img width="494" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/e9a87aca-ba0f-4ce6-a39e-1e1d3796c9e3">

同じ変数を他の要素にも使って、ボタンを押すだけで **複数の要素を同時に切り替える** こともできます。

さらに、**Layout-Wide Loading Requirements** を使えば、レイアウト全体を切り替えることもできます。レイアウト全体の要件を設定するには、エディタの背景を右クリックします。ただし、切り替えたいレイアウトではなく、別のレイアウトにボタンを追加するようにしてください。

# 順番に切り替える

2つの値を切り替えるのとは異なり、値を順番に切り替えるには、アクションスクリプトが2つ以上の値の間を循環できる必要があります。

アクションスクリプトのロジックは切り替えの場合とかなり似ているので、ここでは簡潔に説明します。切り替えの説明もあわせて読んでください。

画像を3枚追加しました。1枚目は変数の値が `1` のときに表示され、2枚目は値が `2` のとき、3枚目は値が `3` のときに表示されます。

<br>
<img width="494" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/731c13cf-6f81-470b-8e1b-cba264ffbe05">

その後、循環用のボタンを追加し、変数の値が `1` → `2` → `3` → `1` と切り替わるようにしました。

<br>
<img width="609" alt="Screenshot_1" src="https://gist.github.com/assets/35544624/9f2052b1-8d3d-4a35-884a-4a234e63d5e5">

これで完了です。レイアウトを保存し、エディタを終了して、循環ボタンが正しく動作するか確認してください。

<br>
<img width="494" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/430c2369-a43f-4d0f-9203-3fdb1b9eae2c">
