# MusicBoxApi

[![Software License](https://img.shields.io/badge/license-MIT-brightgreen.svg)](LICENSE.txt)
[![versions](https://img.shields.io/pypi/v/MusicBoxApi.svg)](https://pypi.python.org/pypi/MusicBoxApi/)
[![platform](https://img.shields.io/badge/python-2.7-green.svg)]()
[![platform](https://img.shields.io/badge/python-3.5-green.svg)]()

从 musicbox 网易云音乐 CLI 播放器抽离出来的 API ，去掉了界面相关的逻辑，方便在其他程序中复用。

## 安装

``` sh
pip install MusicBoxApi
```

## 使用示例

``` py
from MusicBoxApi import api as NetEaseApi

def get_top_songlist():
    netease = NetEaseApi.NetEase()
    music_list = netease.top_songlist()
    datalist = netease.dig_info(music_list, 'songs')
    playlist = []
    for data in datalist:
        music_info = {}
        music_info.setdefault("song_name", data.get("song_name"))
        music_info.setdefault("artist", data.get("artist"))
        music_info.setdefault("album_name", data.get("album_name"))
        music_info.setdefault("mp3_url", data.get("mp3_url"))
        music_info.setdefault("playTime", data.get("playTime"))
        music_info.setdefault("quality", data.get("quality"))
        playlist.append(music_info)
    return playlist

print(get_top_songlist())
```
