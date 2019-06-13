---?color=#3A8FB7

@snap[headline]
# Unityを使って<br>タイピングゲームを<br>作ってみよう
@snapend


---

### アセットを選択する
1. 画面上部のメニューから **Assets** をクリック
2. **Assets** > **ImportPackage** > **CustomPackage...** をクリック
3. **デスクトップ** > **TheWaggleTypingGame.unitypackage** を選択
4. **開く** をクリック

---

### アセットをインポートする
1. 出てきたウィンドウにある **Import** をクリック

---

### インポートされたことを確認する

1. **Project** ウィンドウの中に表示が増えたことを確認

---

### 新規シーンを作成する

1. 画面上部のメニューから **File** をクリック
2. **File** > **New Scene** をクリック

---?color=#3A8FB7

### シーンとは

シーンは映画の1シーンの撮影セットのようなもの

舞台があって
その上にキャラクターや物があって
それをライトが照らし
カメラが映し出します

これら全てを
創ったり配置したりするのがシーンです

シーン上にあるカメラから映し出された映像が
ゲームの1シーンになります

---?image=assets/img/SaveScene.png&size=auto 60%&position=bottom
@title[シーンを保存する]

@snap[north-west]
<h2>@size[0.7em](シーンを保存する)</h2>
<b>File</b> > <b>Save Scene</b> をクリックしてください<br>
シーンに名前をつけて保存します
@snapend

---?image=assets/img/SaveScene2.PNG&size=60% auto
@title[シーン名を入力する]

@snap[north-west]
<h2>@size[0.7em](シーン名を入力する)</h2>
<b>ファイル名</b>に <b>Main</b> と入力して<br>
<b>保存</b> ボタンをクリックしてください
@snapend

---?image=assets/img/CreatedMain.PNG&size=auto 70%&position=bottom
@title[シーンが作成されたことを確認する]

@snap[north-west]
<h2>@size[0.7em](シーンが作成されたことを確認する)</h2>
このように <b>Main</b> と表示されれば保存成功です
@snapend

---
@title[プレハブをインスタンス化する]

@snap[north-west]
<h2>@size[0.7em](プレハブをインスタンス化する)</h2>
<p>
  <b>Assets</b> > <b>＿Prefabs</b> にある以下のものを<br>
  <b>Hierarchy</b>にドラッグ&ドロップしてください
</p>
<ul>
  <li>BackgroundMusic</li>
  <li>Floor</li>
  <li>GameManager</li>
  <li>HUDCanvas</li>
  <li>MainCamera</li>
  <li>MiniMapCamera</li>
  <li>Player</li>
</ul>
@snapend

---
@title[プレハブとインスタンス化]

<h2>@size[0.7em](プレハブとインスタンス化)</h2>
<p>
  プレハブとは、アセットの中でも<br>
  <b>部品化するだけでそのまま動き出す</b>ものです
</p>
<p>
  <i>Project</i> ウィンドウから <i>Hierarchy</i> ウィンドウに<br>
  ドラッグ&ドロップすることで<br>
  実際のオブジェクトになります
</p>
<p>
  この動作を<b>インスタンス化</b>といい<br>
  実体化されたオブジェクトを<b>インスタンス</b>といいます
</p>

---
@title[キー入力の設定]

<h2>@size[0.7em](キー入力の設定)</h2>
どのキー入力を何の処理として受け付けるかという設定

今回は、デフォルト設定の入力処理が
文字のタイピングと重複しないように消します

  - **Edit** > **ProjectSettings** > **Input** をクリック
    - **Axis**  > **Vertical** > **Horizontal** から **a** , **d** を消去
    - **Axis**  > **Vertical** > **Vercal** から **s** , **w** を消去

---
@title[スカイボックスの設定]

@snap[north-west]
<h2>@size[0.7em](スカイボックスの設定)</h2>
@snapend

  - **Window** > **Rendering** > **Lighting Settings** をクリック
    - **Skybox Material** のサークルセレクトをクリック
    - **NightmaresProceduralSkybox** をダブルクリック

---
@title[レイヤーの設定]
<h2>@size[0.7em](レイヤーの設定)</h2>
レイヤーとはゲームオブジェクトのグループ分けをするもの

今回は、マウスの位置を取得するためのオブジェクトを
レイヤーを利用して設定します

  - **Inspector** > **Layer** > **Add Layer** をクリック
    - 空いている一番上の欄に **Floor** と記入
    - **Hierarchy** > **Floor** > **MousePointingFloor** をクリック
    - レイヤーを **Floor** に設定

---
@title[ナビメッシュの設定]

<h2>@size[0.7em](ナビメッシュの設定)</h2>
ナビメッシュとはゲームオブジェクトが動く経路を
自動探索させるために設定する可動範囲のこと

  - **Hierarchy** > **Floor** > **NavMeshWalkableFloor** をクリック
    - **MeshRenderer** のチェックボックスを **チェックがついた状態** にする
  <!--  - **AddComponent** をクリックして **MeshRenderer** を選択-->
    - **Window** > **AI** > **Navigation** をクリック
    - **Bake** タブにある **Bake** ボタンをクリックする
    - **MeshRenderer** のチェックボックスを **チェックが外れた状態** にする

---
@title[MainCameraとDirectionalLightの削除]

<h2>@size[0.7em](MainCameraとDirectionalLightの削除)</h2>

シーンを新規作成したときに
デフォルトで生成されていたカメラとライトを
右クリックして **Delete** する

  - **Hierarchy** > **MainCamera** を削除
  - **Hierarchy** > **DirectionalLight** を削除

---
@title[シーンをリロードできるように設定]

<h2>@size[0.7em](シーンをリロードできるように設定)</h2>
ゲームオーバーになったときに
シーンがリロードされるように設定する

  - **File** > **Build Settings** をクリックする
    - **Add Open Scenes** をクリックする

---
@title[動きを確かめる]

<h2>@size[0.7em](動きを確かめる)</h2>

1. **Game** > **Maximize On Play** をクリックする
1. 動きを確かめる

  - @size[0.7em](矢印キーの押された方向にプレーヤーが動く)
  - @size[0.7em](マウスのある方向にプレーヤーが向く)
  - @size[0.7em](正しくキー入力をするとエネミーの問題文が赤文字に代わる)
  - @size[0.7em](エネミーの問題文をすべて入力するとエネミーが死ぬ)
  - @size[0.7em](エネミーはプレーヤーを自動で追いかけ続ける)
<!--  - @size[0.7em](プレーヤーもエネミーも障害物を避けて進む)-->
  - @size[0.7em](プレーヤーのHPが0になるとゲームオーバーになり リスタートする)

---
@title[問題なければ最後に]

<h2>@size[0.7em](問題なければ最後に)</h2>

1. **Project** > **Assets** > **＿Prefabs** > **Lights** をインスタンス化
1. **Project** > **Assets** > **＿Prefabs** > **Environment** をインスタンス化

<!--1. **Window** > **Rendering** > **Lighting Settings**をクリックする-->
<!--  - **Auto Generating** をクリックしてチェックを外す-->
<!--  - **Generate Lighting** をクリックする-->

---
@title[トライしてみよう]

<h2>トライしてみよう</h2>

---
@title[エネミーの問題文を変えるには]

<h2>@size[0.7em](エネミーの問題文を変えるには)</h2>

1. **Project** > **Assets** > **＿Resources** をクリックする
  - **TypingText** をダブルクリックする
  - 一行に一単語を入力する
    ※半角英字（小文字）だけを使う設定になっています
  - 保存する
1. **Project** > **Assets** > **＿Resources** をクリックする
  - **Inspector** で新しいデータに書き換わっていることを確認する

これでエネミーの問題文が新しいデータに変わります

---
@title[プレーヤーHPの設定]

<h2>@size[0.7em](プレーヤーのHP設定)</h2>

プレーヤーのHPを変える

1. **Hierarchy** > **Player** をクリック
  - **Inspector** > **Player Health Controller** > **Starting Health** の値を変更する
1. **Hierarchy** > **HUDCanvas** > **HealthUI** > **HealthSlider** をクリック
  - **Slider** > **MaxValue** を変更した値に変える
  - **Slider** > **Value** を最大値に変える

---
@title[プレーヤーのスピード設定]

<h2>@size[0.7em](プレーヤーのスピード設定)</h2>

プレーヤーの動くスピードを変える

1. **Hierarchy** > **Player** をクリック
1. **Inspector** > **Player Movement Controller** > **Speed** の値を変更する

---
@title[エネミーのスピード設定]

<h2>@size[0.7em](エネミーのスピード設定)</h2>

エネミーの動くスピードを変える

1. **Project** > **Assets** > **OtherPrefabs** > **Charactors** をクリック
1. スピードを変更したいエネミーをクリック
1. **Inspector** > **Enemy Movement Controller** > **Speed** の値を変更する

---?image=assets/img/Scripting2.PNG&size=100% auto&position=bottom
@title[スクリプトを触ってみる]

@snap[north-west]
<h2>@size[0.7em](スクリプトを触ってみる)</h2>

<b>Assets</b> > <b>Scripts</b> > <b>GameManager</b> > <b>GameController.cs</b> をダブルクリックして<br>
画像の通りに104行目に<b>Debug.Log()</b>を入れてみる
@snapend

---
@title[ゲームオブジェクトを作ってみる]

<h2>@size[0.7em](MiniMapを作ってみる)</h2>

1. **Hierarchy** > **MiniMapCamera** をクリックして **Inspector** 内の一番上にあるチェックを外す
1. **Hierarchy** > **Create** > **Camera** をクリック
1. 名前を **MiniMap** に変更
1. **Inspector**の全ての値を **MiniMapCamera** の通りに設定
1. 全体を真上から移すカメラとして動いていることを確認
