```
❯ yay -S zed
Sync Explicit (1): zed-0.225.10-1
[sudo] password for takuya:
resolving dependencies...
:: There are 15 providers available for vulkan-driver:
:: Repository extra
   1) nvidia-utils  2) vulkan-asahi  3) vulkan-broadcom  4) vulkan-dzn  5) vulkan-freedreno  6) vulkan-gfxstream
   2) vulkan-intel  8) vulkan-kosmickrisp  9) vulkan-nouveau  10) vulkan-panfrost  11) vulkan-powervr  12) vulkan-radeon
   3) vulkan-swrast  14) vulkan-virtio
:: Repository omarchy
   4) nvidia-580xx-utils

```

インストールしようとしたら`vulkan`のドライバをどれにするか聞かれた。
`vulkan`は低レベルなGPUのAPI。パフォーマンスが悪かったら違うのに変えるけど、とりあえずデフォルトの`nvidia-utils`にしてみた。

