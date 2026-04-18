# Windowsの環境構築
windowsをクリーンインストールしたときに, 環境を再構築するための手順を残す.

## 目次
- [OneDrive](#onedrive)
- [Chrome](#chrome)
- [AviUtl2](#aviutl2)
- [Discord](#discord)
- [Git](#git)
- [PowerToys](#powertoys)
- [VScode](#vscode)
- [VOICEVOX](#voicevox)

## OneDrive
OneDriveをwindows環境から除去する.

### アカウントの同期を解除
1. タスクバーに常駐しているOneDriveアイコンを右クリック
2. **設定**を選択
3. リンクを解除する

### アンインストール
1. 管理者権限でターミナルを起動
2. 以下のコマンドを実行

64bit環境
```
taskkill /f /im OneDrive.exe
%SystemRoot%\SysWOW64\OneDriveSetup.exe /uninstall
```
32bit環境
```
taskkill /f /im OneDrive.exe
%SystemRoot%\System32\OneDriveSetup.exe /uninstall
```

### 再インストールの予防
1.  [win]+Rから**gpedit.msc**を実行
2. [コンピュータの構成]>[管理者用テンプレート]>[Windowsコンポーネント]>[OneDrive]へ移動
3. [OneDriveをファイル記憶域として使用できないようにする]を選択
4. [有効]をチェックして[OK]を選択

### フォルダ自動生成の停止
1. [Win]+Rからregeditを実行
2. 以下のパスに移動
`HKEY_CURRENT_USER\Sofrware\Microsoft\Windows\CurrentVersion\Explorer\User Shell Folders`
3. リストの値に**OneDrive**が含まれている場合は修正する

### キャッシュの削除
1. 管理者権限でターミナルを起動
2. 以下のコマンドを実行
```
rd /s /q "%UserProfile%\OneDrive"
rd /s /q "%LocalAppData%\Microsoft\OneDrive"
rd /s /q "%ProgramData%\Microsoft OneDrive"
```

## Chrome
[Google Chrome](https://www.google.com/intl/ja_jp/chrome/)をダウンロードする.

## AviUtl2
[AviUtl2](https://spring-fragrance.mints.ne.jp/aviutl/)をダウンロードする.

## Discord
[Discord](https://discord.com/)をダウンロードする.

## Git
[Git](https://gitforwindows.org/)をダウンロードする.
1. インストーラーを起動する
2. デフォルトエディタをVScodeにする
3. HTTPS transport backendをOpenSSL libraryにする
4. extra optionsは両方ともにチェックを入れる

### 環境設定
ユーザー名とメールアドレスを設定
```
git config --global user.name "hoge"
git config --global user.email "fuga"
```
SSHキーを作成
```
ssh-keygen
```


## PowerToys
[PowerToys](https://github.com/microsoft/PowerToys/releases)をダウンロードする.

## VScode
[VScode](https://code.visualstudio.com/)をダウンロードする.

### 拡張機能
以下の拡張機能をインストールする.
- Japanese Language Pack for Visual Studio Code
- JavaScript (ES6) code snippets
- Markdown Checkboxes
- Markdown Footnotes
- Markdown Preview Github Styling

## VOICEVOX
[VOICEVOX](https://voicevox.hiroshiba.jp/)をダウンロードする.