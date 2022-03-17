# AdMob広告について

## 前提条件
* Unity 2019 以上

### Android
* Android 4.4 以上
* minSdkVersion 14以上
* compileSdkVersion 28以上

### iOS

* iOS 10 以上
* Xcode 12.5 以上
* CocoaPods 必須


## 事前準備

[AdMobのスタートガイド](https://developers.google.com/admob/unity/start?hl=ja)を参考に、AdMobの設定をおこなってください。  
[Google Mobile Ads Unity Plugin](https://github.com/googleads/googleads-mobile-unity/releases)は、v7.0.0以上のものをご利用ください。

### メディエーションの準備

[AdMobメディエーション](https://developers.google.com/admob/unity/mediate?hl=ja)を行うために、adstirのAdMobパッケージ版のUnityプラグインをインポートします。  
AdMobパッケージ版のUnityプラグインの入手は、営業担当にご連絡いただくか[お問い合わせ](https://ja.ad-stir.com/contact)ください。  
Unityプラグインのインポート及びSDKの導入については、[こちら](../adstir/init.md)を参考にしてください。

## 広告の実装

AdMobの実装ガイドをご覧ください

* [バナー](https://developers.google.com/admob/unity/banner?hl=ja)
* [インタースティシャル](https://developers.google.com/admob/unity/interstitial?hl=ja)
* [動画リワード](https://developers.google.com/admob/unity/rewarded-ads?hl=ja)

### テストデバイスの追加
[開発時にはテスト端末を追加する](https://developers.google.com/admob/unity/test-ads?hl=ja#add_your_test_device)より、広告リクエスト時にデバイスIDの設定をおこなってください。  
こちらの設定をおこなった際には、アプリケーションのリリース前には該当コードの削除をお願いいたします。
