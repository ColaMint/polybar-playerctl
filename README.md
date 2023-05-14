# polybar-netease-cloud-music

polybar modules for netease-cloud-music

![polybar-netease-cloud-music](./screenshot.png)

# modules

```
[module/netease-cloud-music-previous]
type = custom/text
content = 
click-left = /path/to/polybar-netease-cloud-music.sh previous

[module/netease-cloud-music-next]
type = custom/text
content = 
click-left = /path/to/polybar-netease-cloud-music.sh next

[module/netease-cloud-music-play-pause]
type = custom/script
interval = 1
exec = /path/to/polybar-netease-cloud-music.sh is-playing && echo  || echo 
click-left = /path/to/polybar-netease-cloud-music.sh play-pause

[module/netease-cloud-music-title]
type = custom/script
interval = 1
exec = /path/to/polybar-netease-cloud-music.sh title || echo 启动网易云音乐
click-left = /path/to/polybar-netease-cloud-music.sh launch
```

If the desktop file for Netease Cloud Music is not located in `/usr/share/applications/netease-cloud-music.desktop`, please modify the `DESKTOP_PATH` in `polybar-netease-cloud-music.sh` on your own.
