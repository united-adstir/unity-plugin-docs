# バナー広告の導入

## 対応OS
- Android 4.4 以上
- iOS 9.0 以上

## 広告の設置
### 実装例
1. `Hierarchy`から`Main Camera`等を選択し`Inspector->Add Component->Script`をクリックします。
1. `Adstir Plugin`を選択して、追加します。
1. `Plugins/AdstirPlugin.cs`のOnEnableとOnDisableをアンコメントします。
1. `MEDIA-ID`および`SPOT-ID`は管理画面で取得した`メディアID`と`枠No`に置換してください。

```c#
public void OnEnable()
{
    this.ShowAd("MEDIA-ID",SPOT-ID,0,0,320,50);
}
	
public void OnDisable()
{
    this.HideAd();
}
```

### 座標による指定

下記いずれかのメソッドを使用して指定することができます。

#### X, Y座標を指定

```c#
this.ShowAd(string media, int spot, int x, int y, int w, int h);
```

#### Layout列挙型で指定

```c#
this.ShowAd(string media, int spot, int w, int h, Layout layout);
```

Layout列挙型は以下のいずれかを使用できます。

||縦位置|横位置|
|:--|:--|:--|
|Top|上|中央|
|TopLeft|上|左|
|TopRight|上|右|
|Center|中央|中|
|CenterLeft|中央|左|
|CenterRight|中央|右|
|Bottom|下|中|
|BottomLeft|下|左|
|BottomRight|下|右|

### 対応している広告サイズ
  - 320x50
  - 320x100
  - 300x250
