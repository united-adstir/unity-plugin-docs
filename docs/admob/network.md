# AdMobメディエーションで利用できるアドネットワーク

## アドネットワーク一覧
adstirのAdMobパッケージには下記のアドネットワークのSDKがパッケージングされております。

アドネットワーク|バナー|インタースティシャル|動画リワード|動画リワード(新API)
---|:-:|:-:|:-:|:-:
AdColony| o | o | o | o 
AppLovin| o | o | o | o 
maio    | - | o | o | o 
MoPub   | o | o | o | o 
nend    | o | o | o | o 
Tapjoy  | - | o | o | o 
UnityAds| o | o | o | o 

※ MoPub / maioはAndroidのみ

## 追加実装

アドネットワークによっては追加実装が必要なネットワークがございます。下記を参照して実装をお願いします。

### MoPubの追加実装


[こちら](https://bintray.com/google/mobile-ads-adapters-unity/download_file?file_path=GoogleMobileAdsMoPubMediation%2F2.9.0%2FGoogleMobileAdsMoPubMediation-2.9.0.zip)から`GoogleMobileAdsMoPubMediation.unitypackage`をダウンロードし、Unityプラグインをインポートしてください。  
インポート後に下記を参考に、MoPub SDKの初期化を行ってください。  
`MOPUB_AD_UNIT_ID`は営業担当よりおしらせします。  

```java hl_lines="1 4 5 6 7 8 10 11"
using GoogleMobileAds.Api;
using GoogleMobileAds.Api.Mediation.MoPub;

public class GoogleMobileAdsDemoScript : MonoBehaviour
{
    public void Start()
    {
        MobileAds.Initialize(appId);
        MoPub.Initialize("MOPUB_AD_UNIT_ID");
    }
}
```