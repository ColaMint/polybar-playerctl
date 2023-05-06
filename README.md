# polybar-netease-cloud-music

polybar modules for netease-cloud-music

![polybar-netease-cloud-music](./screenshot.png)

# modules

```
[module/netease-cloud-music-previous]
type = custom/text
content = ""
click-left = "dbus-send --print-reply --dest=org.mpris.MediaPlayer2.netease-cloud-music /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Previous"

[module/netease-cloud-music-next]
type = custom/text
content = ""
click-left = "dbus-send --print-reply --dest=org.mpris.MediaPlayer2.netease-cloud-music /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Next"

[module/netease-cloud-music-pause-or-play]
type = custom/script
interval=1
exec = pgrep -af netease-cloud-music | grep -v pgrep > /dev/null && dbus-send --print-reply --dest=org.mpris.MediaPlayer2.netease-cloud-music /org/mpris/MediaPlayer2 org.freedesktop.DBus.Properties.Get string:'org.mpris.MediaPlayer2.Player' string:'PlaybackStatus' | grep Playing > /dev/null && echo  || echo 
click-left = "dbus-send --print-reply --dest=org.mpris.MediaPlayer2.netease-cloud-music /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.PlayPause"

[module/netease-cloud-music-title]
type = custom/script
interval=1
exec = pgrep -af netease-cloud-music | grep -v pgrep > /dev/null && echo `dbus-send --print-reply --dest=org.mpris.MediaPlayer2.netease-cloud-music /org/mpris/MediaPlayer2 org.freedesktop.DBus.Properties.Get string:'org.mpris.MediaPlayer2.Player' string:'Metadata' | grep "xesam:artist" -A 2 | tail -n1 | sed -e 's/^[ \t]*string *\"//' -e 's/"$//';echo ':';dbus-send --print-reply --dest=org.mpris.MediaPlayer2.netease-cloud-music /org/mpris/MediaPlayer2 org.freedesktop.DBus.Properties.Get string:'org.mpris.MediaPlayer2.Player' string:'Metadata' | grep "xesam:title" -A 1 | tail -n1 | sed -e 's/^[ \t]*variant *string *\"//' -e 's/"$//'` || echo "启动网易云音乐"
click-left = $(grep '^Exec' /usr/share/applications/netease-cloud-music.desktop | tail -1 | sed 's/^Exec=//' | sed 's/%.//' | sed 's/^"//g' | sed 's/" *$//g')
```
