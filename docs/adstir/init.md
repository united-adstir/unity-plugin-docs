# 初期設定

## Unityプラグインの入手
管理画面にログインして、対象の枠の「タグ/SDK」を選択してください。  
「SDKダウンロード」より「adstir SDK (Unityプラグイン)」をダウンロードしてください。  
動画リワード広告または全画面インタースティシャル広告をご利用の場合は、「動画SDK (Unityプラグイン)」をダウンロードしてください。

## Unityプラグインのインポート
組み込みたいプロジェクトを開き、[Assets] > [Import Package] > [Custom Package] より、Unityプラグインを選択します。  
すべてのファイルのチェックボックスがオンになっていることを確認して、[Import] をクリックします。

<img src="../images/init_01.png" width="50%">

## SDKの追加
本プラグインには、[Play Services Resolver](https://github.com/googlesamples/unity-jar-resolver)が同梱されています。  
Play Services Resolverを使用して、iOS/AndroidのSDKをプロジェクトに追加します。  

### Android
[File] > [Build Settings...] から設定画面を開き、「Platform」を「Android」に設定します。

<img src="../images/init_02.png" width="50%">

[Assets] > [Play Services Resolver] > [Android Resolver] > [Resolve] を選択し、SDKを追加します。

<img src="../images/init_03.png" width="50%">

### iOS
iOSのSDKは、ビルド時に[CocoaPods](https://cocoapods.org/)によって追加されます。  
SDKを追加する特別な手順はありません。