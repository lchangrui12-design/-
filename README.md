
****裝環境參考影片****
https://www.youtube.com/watch?v=-z1DcFsZlpc&t=2s    //後面步驟可能不一樣


1) 先準備
1.Windows 10/11
2.需要網路（下載 SDK / Gradle / system image）
3.vs_code


2) 安裝 Flutter（Stable）

下載 Flutter SDK（stable）解壓到例如：
C:\src\flutter(看你要壓哪)

把 C:\src\flutter\bin 加到系統 PATH  //看影片

開 PowerShell 驗證有無下載：

flutter --version
flutter doctor

有跑出東西代表有!!!!


3)開vs_code

  左邊欄位 按"extension" 分別搜尋 Dart 跟Flutter並下載


4)安裝 Android Studio（含 Android SDK / Emulator）//
安裝 Android Studio（預設選項即可）

開 Android Studio → SDK Manager

SDK Platforms：至少裝 Android 14 (API 34)

SDK Tools：勾選

✅ Android SDK Platform-Tools

✅ Android SDK Build-Tools

✅ Android Emulator

✅ Android SDK Command-line Tools (latest)

套用後關閉



5) 建立模擬器（建議 Android 14 / API 34）

Android Studio → More Actions → Virtual Device Manager / Device Manager

Create Device → Pixel 6/7

System Image 選：

✅ Android 14 (API 34) x86_64（建議 Google APIs）

開啟 emulator（按 ▶️）

驗證：

flutter devices


要看到 emulator 類似：
emulator-5554 • android-x64

6) 下載並執行我的專案

取得專案資料夾（例如 flutter_application_1）

進入專案根目錄（要看得到 pubspec.yaml）

cd <你的專案路徑>\flutter_application_1
dir pubspec.yaml


安裝依賴：

flutter pub get


在 emulator 上跑：

flutter run -d emulator-5554


********* 常見問題**********

A) No pubspec.yaml found

→ 代表沒 cd 到專案根目錄，請確認 dir pubspec.yaml 有檔案。

B) emulator 很新（Android 16 / API 36）導致 debug 卡住

→ 建議改用 Android 14 (API 34) emulator，比較穩。

C) Waiting for VM Service port... 卡住

→ 先重啟 adb + 清除 forward：

& "$env:LOCALAPPDATA\Android\Sdk\platform-tools\adb.exe" kill-server
& "$env:LOCALAPPDATA\Android\Sdk\platform-tools\adb.exe" start-server
& "$env:LOCALAPPDATA\Android\Sdk\platform-tools\adb.exe" -s emulator-5554 forward --remove-all
flutter run -d emulator-5554




