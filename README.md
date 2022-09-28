<div style="text-align: right;">
VK_CONVERT patch for ultravnc vncviewer 2022-09-15
</div>

# VK_CONVERT の keysym を変更する

## やりたい事
UltraVNC vncviewer で `変換`キー を keysym Henkan_Mode で使いたい。

## 背景
Windows から Linux 系のマシンを GUI で操作する際に UltraVNC vncviewer を日本語キーボードに設定して[^1]使っています。また普段 Windows、Linux どちらも IME の ON/OFF は、スペース キー の右側にある `変換`キー で **ON**、左側にある `無変換`キー で **OFF** しています（キーの割当ては Microsoft IME や Mozc 等の設定で指定）。しかし、UltraVNC vncviewer の `変換`キー は keysym Mae_Koho に設定されているため、それができません。

## `変換`キー の keysym を Henkan_Mode に設定した UltraVNC vncviewer を作る
vncviewer/KeyMapjap.cpp にパッチを当ててビルドします（パッチを当てると言っても、VK_CONVERT の設定を XK_Mae_Koho から XK_Henkan_Mode にするだけですので、手で変更した方が早そうです）。

- このパッチは [UltraVNC](https://uvnc.com/) vncviewer 1.3.8.0 で作りました。
- UltraVNC vncviewer の 開発環境の整備 や ソースコード入手 については、https://github.com/ultravnc/ultravnc に説明があります。
- ビルドする際に、[Forum](https://forum.uvnc.com/) の Developer discussions (mainly user-mode) にある Compiling source code in Visual Studio 2017 を参考にしました。また、Visual Studio 2017 を使用し、ソリューション 構成:Debug、プラットフォーム:Win32 でビルドしました。

[^1]: Option の Mouse and Keyboard で Japanese keyboard を選択
