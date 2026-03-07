https://gihyo.jp/book/2025/978-4-297-14859-1

# 環境構築

```
❯ clang --version
clang version 21.1.8
Target: x86_64-pc-linux-gnu
Thread model: posix
InstalledDir: /usr/bin

~
❯ make --version
GNU Make 4.4.1
Built for x86_64-pc-linux-gnu
Copyright (C) 1988-2023 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <https://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.
```

`clang`と`make`は元々入ってたから、`qemut`と`nc`をいれる

```
❯ yay -S qemu-system-x86 openbsd-netcat-git
```

rust の toolchain のバージョンは書いてある通りにする。

Hello World を qemu で動かそうとしたときに画面が出ずに下のようなログで止まった。

```
VNC server running on `::1:5900'
```

画面を出すバックエンド？みたいなのが足りてないみたい。qemu 関連を全部持ってくるという力技で解決。

```
yay -S qemu-full
```

## 2 章

UEFI のアプリケーションを書いていく。[UEFIの仕様書はこちら](https://uefi.org/specs/UEFI/2.11/)

no_std, no_main で無限ループするバイナリを `objdump`した。

```
target/x86_64-unknown-uefi/debug/wasabi.efi:     file format pei-x86-64


Disassembly of section .text:

0000000140001000 <.text>:
   140001000:	eb 00                	jmp    0x140001002
   140001002:	eb fe                	jmp    0x140001002
```

`140001000`からプログラムは始まってるようす

`repr(C)`は構造体のメモリレイアウトをC言語仕様に指定するもの。rustでは無駄なパディングを発生させないために構造体のメンバーを並び替える。UEFIはC言語を前提にしているのでメモリレイアウトを揃える必要がある。[公式ドキュメント](https://doc.rust-jp.rs/rust-nomicon-ja/other-reprs.html)や[このブログ](https://ryochack.hatenablog.com/entry/2018/03/23/184943)に詳しく載っている。

EFI Graphics Output Protocol は[ここで定義されている](https://uefi.org/specs/UEFI/2.11/12_Protocols_Console_Support.html#graphics-output-protocol)

