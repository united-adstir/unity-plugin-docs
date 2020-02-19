# 動画リワード広告

## 対応OS

Android4.4以上
iOS 9以上

## 広告の設定

### 1.メディアユーザIDの設定
サーバーサイドで成果通知を受け取る場合、メディアユーザーIDを設定します。  
メディアユーザIDの設定は、`動画広告の初期化`よりも前までに設定する必要があります。

```c#
AdstirVideoAds.SetMediaUserID("xxx@xxx.xx");
```

### 2.動画広告の初期化

はじめに、`AdstirVideoAds.Init()`を使い、プロジェクトで利用する全ての動画広告の初期化を同時に行います。  
動画リワード広告と[全画面インタースティシャル広告](../interstitial.md)を併用する場合は、同時に初期化を行う必要があります。

```c#
int[] spotNos = new int[] { 1, 2 };
AdstirVideoAds.Init("MEDIA-xxxxxx", spotNos);
```

### 3.リスナーの設定

動画リワード広告のイベント通知を行うリスナーを設定します。

```c# hl_lines="1 2 3 12"
public void Start()
{
    ...
    AdstirVideoReward.OnLoad = OnLoad;
    AdstirVideoReward.OnFailToLoad = OnFailToLoad;
    AdstirVideoReward.OnStart = OnStart;
    AdstirVideoReward.OnFailToStart = OnFailToStar;t
    AdstirVideoReward.OnComplete = OnComplete;
    AdstirVideoReward.OnCancel = OnCancel;
    AdstirVideoReward.OnFinish = OnFinish;
    AdstirVideoReward.OnClose = OnClose;
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

public void OnComplete(int spot)
{
    // リワードが発生した時の処理を書きます
}

public void OnCancel(int spot)
{
    // リワードの発生が失敗した時の処理を書きます
}

public void OnFinish(int spot)
{
    // 動画の再生が終了した時の処理を書きます
}

public void OnClose(int spot)
{
    // 動画が閉じられた時の処理を書きます
}
```

### 4.動画リワード広告の読み込み

動画リワード広告の読み込みを行います。

```c#
// 指定した枠Noの動画リワード広告を読み込みます。
AdstirVideoReward.Load(spot);
```

### 5.動画リワード広告の再生

読み込みが完了した動画リワード広告を再生します。
動画の再生後、もう一度動画を再生するためには`4.動画リワード広告の読み込み`を行う必要があります。

```c#
// 再生可能状態を確認してから再生します。
if (AdstirVideoReward.CanShow(spot))
{
    AdstirVideoReward.Show(spot);
}
```

## 動画リワード広告の実装例

```c#
using UnityEngine;

public class AdstirReward : MonoBehaviour
{
#if UNITY_ANDROID
    private const string media = "MEDIA-xxxxxx";
    public static int spot = 2;
#elif UNITY_IPHONE
    private const string media = "MEDIA-xxxxxx";
    public static int spot = 2;
#else
    private const string media = null;
    public static int spot = 0;
#endif


    public void Start()
    {
        AdstirVideoAds.SetMediaUserID("xxx@xxx.xx");
        int[] spotNos = new int[] { 1, 2 };
        AdstirVideoAds.Init("MEDIA-xxxxxx", spotNos);

        AdstirVideoReward.OnLoad = OnLoad;
        AdstirVideoReward.OnFailToLoad = OnFailToLoad;
        AdstirVideoReward.OnStart = OnStart;
        AdstirVideoReward.OnFailToStart = OnFailToStart;
        AdstirVideoReward.OnComplete = OnComplete;
        AdstirVideoReward.OnCancel = OnCancel;
        AdstirVideoReward.OnFinish = OnFinish;
        AdstirVideoReward.OnClose = OnClose;
    }

    public void Load()
    {
        AdstirVideoReward.Load(spot);
    }

    public void Show()
    {
        if (AdstirVideoReward.CanShow(spot))
        {
            AdstirVideoReward.Show(spot);
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

    public void OnComplete(int spot)
    {
        // リワードが発生した時の処理を書きます
    }

    public void OnCancel(int spot)
    {
        // リワードの発生が失敗した時の処理を書きます
    }

    public void OnFinish(int spot)
    {
        // 動画の再生が終了した時の処理を書きます
    }

    public void OnClose(int spot)
    {
        // 動画が閉じられた時の処理を書きます
    }
}
```


## 成果のコールバックURLへの通知

adstirでは、インセンティブ付与の通知を、任意のコールバックURLに行うことが可能です。
付与するインセンティブの単位と額は、任意の値に変更可能です。
`AdstirVideoAds.SetMediaUserID("xxx@xxx.xx");` でユーザーIDを設定していない場合には通知されませんので、ご注意ください。

[動画インセンティブ付与をコールバックURLに通知する](callback.md)
