---?color=#3A8FB7

@snap[headline]
# Unityを使って<br>タイピングゲームを<br>作ってみよう
@snapend

---

### 内容
1. 見本をプレイしてみよう
2. 自分で作り上げてみよう
3. ゲームを改造してみよう

---?color=#3A8FB7

@snap[headline]
### 1. 見本をプレイしてみよう
@snapend

---

### 新規作成する
1. **Unity** を起動
2. **プロジェクト名** に **TypingGame** と記入
3. **保存場所** に **デスクトップ** を指定
4. **作成** をクリック

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

### 見本のシーンを展開する

1. **Assets** > **＿MyScene** ＞　**Unityマーク** の **MySceneTest** をダブルクリック

---

### レイヤーを設定する

1. **Inspector** > **Layer** > **Add Layer** をクリック
2. 空いている一番上の欄に **Floor** と記入
3. **Hierarchy** > **Floor** > **MousePointingFloor** をクリック
4. レイヤーを **Floor** に設定

---

### プレイする

1. 画面の **上部中央** にある **再生ボタン** をクリック
2. 迫ってくるエネミーの頭の上にある **英単語をタイピング**

---?color=#3A8FB7

@snap[headline]
### 2. 自分で作り上げてみよう
@snapend

---

### 新規シーンを作成する

1. 画面上部のメニューから **File** をクリック
2. **File** > **New Scene** をクリック

---?color=#3A8FB7

### シーンとは

シーンは映画の1シーンのようなもの<br>
<br>
シーンには @css[font-color-white](舞台) があって<br>
その上に @css[font-color-white](キャラクターや物) があって<br>
それを @css[font-color-white](ライト) が照らし<br>
@css[font-color-white](カメラ) が映し出します<br>
@snapend

---

### シーンを保存する

1. **File** > **Save Scene** をクリック
2. **Scenes** をダブルクリック
3. **ファイル名** に **Main** と入力
4. **Save** をクリック

---

### シーンが作成されたことを確認する

1. **Hierarchy** > **Unityマーク** の隣 > **Main** と表示されていることを確認

---

### プレハブを実態化する

1. **Assets** > **＿Prefabs** にある以下のものを **Hierarchy** にドラッグ&ドロップ
  - BackgroundMusic
  - Floor
  - GameManager
  - HUDCanvas
  - MainCamera
  - MiniMapCamera
  - Player

---?color=#3A8FB7

### プレハブ

プレハブとは @css[font-color-white](部品化するだけでそのまま動き出す) もののこと<br>
<br>
@css[font-color-white](Project) ウィンドウから @css[font-color-white](Hierarchy) ウィンドウに<br>
@css[font-color-white](ドラッグ&ドロップ) すると作られる

---

### キー入力の設定

1. **Edit** > **ProjectSettings** > **Input** をクリック
2. **Axis**  > **Vertical** > **Horizontal** から **a** , **d** を消去
3. **Axis**  > **Vertical** > **Vercal** から **s** , **w** を消去

（a,d,s,w キーの入力で上下左右に移動しないように<br>
デフォルト設定を削除する）

---

### スカイボックスの設定

1. **Window** > **Rendering** > **Lighting Settings** をクリック
2. **Skybox Material** の **サークルセレクト**（小さいドーナツ）をクリック
3. **NightmaresProceduralSkybox** をダブルクリック

---

### レイヤーの設定

1. **Inspector** > **Layer** > **Add Layer** をクリック
2. 空いている一番上の欄に **Floor** と記入
3. **Hierarchy** > **Floor** > **MousePointingFloor** をクリック
4. レイヤーを **Floor** に設定
    
（レイヤーとはゲームオブジェクトのグループ分けをするもの）<br>
（今回はマウスの位置を取得するために利用）

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
