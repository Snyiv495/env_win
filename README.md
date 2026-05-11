# Windowsの環境構築
windowsをクリーンインストールしたときに, 環境を再構築するための手順を残す.

## 目次
- [Windowsの環境構築](#windowsの環境構築)
  - [目次](#目次)
  - [AviUtl2](#aviutl2)
  - [Chrome](#chrome)
  - [Cloudflare](#cloudflare)
  - [Discord](#discord)
  - [Git](#git)
    - [環境設定](#環境設定)
  - [Keyboard](#keyboard)
    - [キーマッピング](#キーマッピング)
    - [IMEの設定](#imeの設定)
  - [nodejs](#nodejs)
  - [OneDrive](#onedrive)
    - [アカウントの同期を解除](#アカウントの同期を解除)
    - [アンインストール](#アンインストール)
    - [再インストールの予防](#再インストールの予防)
    - [フォルダ自動生成の停止](#フォルダ自動生成の停止)
    - [キャッシュの削除](#キャッシュの削除)
  - [PowerToys](#powertoys)
  - [VOICEVOX](#voicevox)
  - [VScode](#vscode)
    - [拡張機能](#拡張機能)

## AviUtl2
[AviUtl2](https://spring-fragrance.mints.ne.jp/aviutl/)をダウンロードする.

## Chrome
[Google Chrome](https://www.google.com/intl/ja_jp/chrome/)をダウンロードする.

## Cloudflare
1. [winget](https://learn.microsoft.com/ja-jp/windows/package-manager/winget/)をダウンロード・インストールする.
2. `winget install --id Cloudflare.cloudflared`コマンドでCloudflareをインストールする.

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

## Keyboard
### キーマッピング
CapsLockをCtrlにして, CtrlをCtrl(right)に変更する.
1.  [win]+Rから**regedit**を実行
2.  `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Keyboard Layout`を選択
3.  右クリックしてから[新規] > [バイナリ]を選択
4.  名前を`Scancode Map`に設定
5.  値をダブルクリックし, `00,00,00,00,00,00,00,00,03,00,00,00,1d,00,3a,00,1d,e0,1d,00,00,00,00,00`を入力
   
### IMEの設定
1.  [設定] > [時刻と言語] >　[言語と地域] > [オプション] > [Microsoft IME] > [全般]を選択
2.  以前のバージョンのIMEを使用を選択
3.  詳細設定を開くを選択
4.  キー設定 : [変更]を選択
5.  変換キーの[入力/...]をIMEをオンに変更
6.  変換キーの上記以外をカタカナに変更
7.  無変換キーの[入力/...]をIMEオフに変更
8.  無変換キーの上記以外をｶﾀｶﾅに変更

## nodejs
1. [nvm](https://github.com/coreybutler/nvm-windows/releases)をダウンロード・インストールする.
2. `nvm list available`コマンドで利用可能なバージョンを確認
3. `nvm install **`コマンドでnodejsをインストールする.
4. `nvm use **`コマンドでnodejsを切り替える

> [!NOTE]
> npmコマンドが利用できないときは, windows power shellを管理者権限で起動し, `Set-ExecutionPolicy RemoteSigned`を実行する.

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

## PowerToys
[PowerToys](https://github.com/microsoft/PowerToys/releases)をダウンロードする.

## VOICEVOX
[VOICEVOX](https://voicevox.hiroshiba.jp/)をダウンロードする.

## VScode
[VScode](https://code.visualstudio.com/)をダウンロードする.

### 拡張機能
以下の拡張機能をインストールする.
- Japanese Language Pack for Visual Studio Code
- JavaScript (ES6) code snippets
- Markdown Checkboxes
- Markdown Footnotes
- Markdown Preview Github Styling
