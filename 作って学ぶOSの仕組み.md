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
