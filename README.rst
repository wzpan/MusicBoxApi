NetEaseMusicApi
===============

NetEase Music Api that comes from musicbox project. Ui-related parts are elimated, so as to be used at other places.

**Install**

.. code:: shell
	  
    pip install MusicBoxApi


**Example**

.. code:: python

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
