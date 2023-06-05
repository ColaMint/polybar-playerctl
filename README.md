# polybar-playerctl

polybar modules for playerctl

![polybar-playerctl](./screenshot.png)

# modules

```
[module/playerctl-previous]
type = custom/text
content = ''
click-left = /path/to/polybar-playerctl.sh previous

[module/playerctl-next]
type = custom/text
content = ''
click-left = /path/to/polybar-playerctl.sh next

[module/playerctl-play-pause]
type = custom/script
interval = 1
exec = /path/to/polybar-playerctl.sh is-playing && echo '' || echo ''
click-left = /path/to/polybar-playerctl.sh play-pause

[module/playerctl-title]
type = custom/script
interval = 1
exec = /path/to/polybar-playerctl.sh title || echo '启动播放器'
click-left = /path/to/polybar-playerctl.sh launch
```

please modify the `PLAYER` and `DESKTOP` in `polybar-playerctl.sh` on your own.
