# 全画面インタースティシャル広告の導入

動画 / 静止画 による全画面広告の導入方法です。

## 対応OS

Android4.4以上  
iOS 9以上

## 広告の設定

### 1.動画広告の初期化を行う

はじめに、`AdstirVideoAds.Init()`を使い、プロジェクトで利用する全ての動画広告の初期化を同時に行います。  
[動画リワード広告](reward/index.md)と全画面インタースティシャル広告を併用する場合は、同時に初期化を行う必要があります。

```c#
int[] spotNos = new int[] { 1, 2 };
AdstirVideoAds.Init("MEDIA-xxxxxx", spotNos);
```

### 2.リスナーの生成

全画面インタースティシャル広告のイベント通知を行うリスナーを設定します。

```c# hl_lines="1 2 3 9"
public void Start()
{
    ...
    AdstirInterstitial.OnLoad = OnLoad;
    AdstirInterstitial.OnFailToLoad = OnFailToLoad;
    AdstirInterstitial.OnStart = OnStart;
    AdstirInterstitial.OnFailToStart = OnFailToStart;
    AdstirInterstitial.OnClose = OnClose;
}

public void OnLoad(int spot)
{
    // 動画の読み込みが完了した時の処理を書きます
}

public void OnFailToLoad(int spot)
{
    // 動画の読み込みが失敗した時の処理を書きます
}

public void OnStart(int spot)
{
    // 動画の再生が開始した時の処理を書きます
}

public void OnFailToStart(int spot)
{
    // 動画の再生が失敗した時の処理を書きます
}

public void OnClose(int spot)
{
    // 動画が閉じられた時の処理を書きます
}
```

### 3.全画面インタースティシャル広告の読み込み

全画面インタースティシャル広告の読み込みを行います。

```c#
// 指定した枠Noの動画リワード広告を読み込みます。
AdstirInterstitial.Load(spot);
```


### 4.全画面インタースティシャル広告の再生

読み込みが完了した全画面インタースティシャル広告を再生します。
動画の再生後、もう一度動画を再生するためには`3.全画面インタースティシャル広告の読み込み`を行う必要があります。

```c#
// 再生可能状態を確認してから再生します。
if (AdstirInterstitial.CanShow(spot))
{
    AdstirInterstitial.Show(spot);
}
```
## 全画面インタースティシャル広告の実装例


```c#
using UnityEngine;

public class AdstirInstl : MonoBehaviour
{
#if UNITY_ANDROID
    private const string media = "MEDIA-xxxxxx";
    public static int spot = 1;
#elif UNITY_IPHONE
    private const string media = "MEDIA-xxxxxx";
    public static int spot = 1;
#else
    private const string media = null;
    public static int spot = 0;
#endif


    public void Start()
    {
        int[] spotNos = new int[] { 1, 2 };
        AdstirVideoAds.Init("MEDIA-xxxxxx", spotNos);

        AdstirInterstitial.OnLoad = OnLoad;
        AdstirInterstitial.OnFailToLoad = OnFailToLoad;
        AdstirInterstitial.OnStart = OnStart;
        AdstirInterstitial.OnFailToStart = OnFailToStart;
        AdstirInterstitial.OnClose = OnClose;
    }

    public void Load()
    {
        AdstirInterstitial.Load(spot);
    }

    public void Show()
    {
        if (AdstirInterstitial.CanShow(spot))
        {
            AdstirInterstitial.Show(spot);
        }
    }

    public void OnLoad(int spot)
    {
        // 動画の読み込みが完了した時の処理を書きます
    }

    public void OnFailToLoad(int spot)
    {
        // 動画の読み込みが失敗した時の処理を書きます
    }

    public void OnStart(int spot)
    {
        // 動画の再生が開始した時の処理を書きます
    }

    public void OnFailToStart(int spot)
    {
        // 動画の再生が失敗した時の処理を書きます
    }

    public void OnClose(int spot)
    {
        // 動画が閉じられた時の処理を書きます
    }
}
```
