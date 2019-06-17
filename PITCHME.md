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
3. **デスクトップ** > **TypingGame.unitypackage** を選択
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

### キー入力を設定する

1. **Edit** > **ProjectSettings** > **Input** をクリック
2. **Axis**  > **Vertical** > **Horizontal** から **a** , **d** を消去
3. **Axis**  > **Vertical** > **Vercal** から **s** , **w** を消去

（a,d,s,w キーの入力で上下左右に移動しないように<br>
デフォルト設定を削除する）

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
2. **Scenes** フォルダをクリック
3. **ファイル名** に **Main** と入力
4. **Save** をクリック

---

### 保存されたことを確認する

1. **Hierarchy** > **Unityマーク** の隣 > **Main** と表示されていることを確認

---

### プレハブを実態化する

1. **Assets** > **＿Prefabs** にある以下の **青いキューブのアイコン** を **Hierarchy** にドラッグ&ドロップ
  - BackgroundMusic
  - Floor
  - GameManager
  - HUDCanvas
  - MainCamera
  - Player

---?color=#3A8FB7

### プレハブとは

プレハブとは @css[font-color-white](部品化するだけでそのまま動き出す) もののこと<br>
<br>
@css[font-color-white](Project) ウィンドウから @css[font-color-white](Hierarchy) ウィンドウに<br>
@css[font-color-white](ドラッグ&ドロップ) すると作られる

---

### スカイボックスを設定する

1. **Window** > **Rendering** > **Lighting Settings** をクリック
2. **Skybox Material** の **サークルセレクト**（小さいドーナツ）をクリック
3. **NightmaresProceduralSkybox** をダブルクリック

---

### レイヤーを設定する

1. **Inspector** > **Layer** > **Floor** があることを確認
2. （なければ）**Inspector** > **Layer** > **Add Layer** をクリック
3. （なければ）空いている一番上の欄に **Floor** と記入
4. **Hierarchy** > **Floor** > **MousePointingFloor** をクリック
5. レイヤーを **Floor** に設定
    
（レイヤーとはゲームオブジェクトのグループ分けをするもの）<br>
（今回はマウスの位置を取得するために利用）

---

### ナビメッシュを設定する

1. **Hierarchy** > **Floor** >　**NavMeshWalkableFloor** > **Add Component** をクリック
2. **MeshRenderer** を検索してクリック
3. **Window** > **AI** > **Navigation** をクリック
4. **Bake** タブ > **Bake** ボタンをクリック
5. **Inspector** > **MeshRenderer** のチェックボックスを **チェックが外れた状態** にする

（ナビメッシュとは、ゲームオブジェクトが動く経路を<br>
自動探索させるために設定する可動範囲のこと）

---

### デフォルトのMainCameraを削除

1. **Hierarchy** > **黒い文字** の **MainCamera** を右クリック > **Delete**をクリック

（自動生成されたデフォルトのカメラは<br>
必要ないので削除する）

---

### シーンをリロードできるように設定

1. **File** > **Build Settings** をクリック
2. **Add Open Scenes** をクリック

（ゲームオーバーになったときに<br>
シーンがリロードされるように設定する）

---

### 動きを確かめる

1. **Game** > **Maximize On Play** をクリック
2. 画面の **上部中央** にある **再生ボタン** をクリック
3. プレイして動きを確認

  - @size[0.7em](矢印キーの押された方向にプレーヤーが動く)
  - @size[0.7em](マウスのある方向にプレーヤーが向く)
  - @size[0.7em](正しくキー入力をするとエネミーの問題文が赤文字に代わる)
  - @size[0.7em](エネミーの問題文をすべて入力するとエネミーが死ぬ)
  - @size[0.7em](エネミーはプレーヤーを自動で追いかけ続ける)
  - @size[0.7em](プレーヤーのHPが0になるとゲームオーバーになり リスタートする)

---

### 問題なければ最後に

1. **Hierarchy** > **黒い文字** の **DirectionalLight** を右クリック > **Delete**をクリック
2. **Project** > **Assets** > **＿Prefabs** > **Lights** を実態化
3. **Project** > **Assets** > **＿Prefabs** > **Environment** を実態化
4. **Window** > **Rendering** > **LightingSettings** > **Generate Lighting** ボタンをクリック

---?color=#3A8FB7

@snap[headline]
# ゲームを改造してみよう
@snapend

---

### プレーヤーの動くスピードを変える

1. **Hierarchy** > **Player** をクリック
2. **Inspector** > **Player Movement Controller** > **Speed** の値を変更

---

### エネミーの動くスピードを変える

1. **Project** > **Assets** > **OtherPrefabs** > **Charactors** をクリック
2. スピードを変更したいエネミーをクリック
3. **Inspector** > **Enemy Movement Controller** > **Speed** の値を変更

---

### プレーヤーのHPを変える

1. **Hierarchy** > **Player** をクリック
2. **Inspector** > **Player Health Controller** > **Starting Health** の値を変更
3. **Hierarchy** > **HUDCanvas** > **HealthUI** > **HealthSlider** をクリック
4. **Slider** > **MaxValue** を変更した値に変更
5. **Slider** > **Value** を最大値に変更

---

### エネミーの問題文を変える

1. **Project** > **Assets** > **＿Resources** をクリック
2. **TypingText** をダブルクリックする
3. 一行に一単語を入力する
  - 半角英字（小文字）だけが使えます
4. 保存する
5. Unityに戻る
6. **Project** > **Assets** > **＿Resources** をクリックする
7. **Inspector** で新しいデータに書き換わっていることを確認する

---
### ゲームオブジェクトを作ってみる

1. **Hierarchy** > **MiniMapCamera** をクリックして **Inspector** 内の一番上にあるチェックを外す
1. **Hierarchy** > **Create** > **Camera** をクリック
1. 名前を **MiniMap** に変更
1. **Inspector** の全ての値を **MiniMapCamera** の通りに設定
1. 全体を真上から移すカメラとして動いていることを確認
