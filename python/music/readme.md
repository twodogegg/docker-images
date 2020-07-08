## 使用
```
docker build -t music .

docker run -it --rm --name music -v /本地目录:/ music 

# 例：
docker run -itd --rm --name music -v /Users/shuliuzhenhua/Music/Music:/usr/src/app music 

docker exec music 后面带命令就好了
```


## 注意
在 docker 容器中若使用 Python2.7 的pip 安装 的 youtube-dl 则会出现 artist - 
track 获取不到的问题

下载mp3
youtube-dl --audio-quality 0  -i --extract-audio --audio-format mp3 --add-metadata  --embed-thumbnail --metadata-from-title "%(artist)s - %(title)s"  -o '%(artist)s - %(title)s.%(ext)s'  https://music.youtube.com/watch?v=nuPTe8SN8es

## 下载最好的视频
```
youtube-dl -f 'bestvideo[ext=mp4]+bestaudio[ext=m4a]/best[ext=mp4]/best' -o '%(title)s.mp4'  https://music.youtube.com/watch?v=_nD1i99prOc
```


## 设置代理
--proxy socks5://127.0.0.:1080/

## 根据搜索下载 mp3

```bash
youtube-dl -f bestaudio/best -o '485232943.mp3'  ytsearch:'安全着陆 个人简介'
```

bestaudio

## 服务器上面下载 MP3
youtube-dl -o '%(artist)s - %(track)s.%(ext)s'  --audio-quality 0  -i --extract-audio --audio-format mp3 https://www.youtube.com/watch?v=1vQ7b1gEfdM

下载mp4
youtube-dl -f bestvideo/best -o '%(title)s.%(ext)s' https://www.youtube.com/watch?v=j6K-lNr360I

搜索
https://www.reddit.com/r/learnpython/comments/3q1wfl/how_to_search_for_videos_in_youtubedl/

下载频道所有视频
youtube-dl -f best -ciw -o "%(title)s.%(ext)s" -v https://www.youtube.com/channel/UCcHWhgSsMBemnyLhg6GL1vA

下载自己顶过的视频
youtube-dl --cookies ../youtube-cookie.text  https://www.youtube.com/playlist?list=LLLMbVf9ipctc0g03RFfWqgQ

下载自己顶过的视频里面的歌曲

【纯享版】胡彦斌/于文文神改编《爱之初体验》 这个没有匹配成功


匹配过滤
--match-filter 
只需要类型是 music 的歌
youtube-dl --match-filter "track !=null" https://www.youtube.com/watch?v=P8MvvvyxknM


下载自己顶过的歌曲
youtube-dl --match-filter "track !=null" -o '%(artist)s - %(track)s.%(ext)s' --audio-quality 0  -i --extract-audio --audio-format mp3 --add-metadata  --embed-thumbnail --metadata-from-title "%(artist)s - %(title)s"  --cookies ../youtube-cookie.text https://www.youtube.com/playlist?list=LLLMbVf9ipctc0g03RFfWqgQ

指定起始位置
 
youtube-dl -o '%(artist)s - %(track)s.%(ext)s' --audio-quality 0  -i --extract-audio --audio-format mp3 --add-metadata  --embed-thumbnail --metadata-from-title "%(artist)s - %(title)s"  --cookies ../youtube-cookie.text --match-filter "track !=null" --playlist-start NUMBER --playlist-end NUMBER  https://www.youtube.com/playlist?list=LLLMbVf9ipctc0g03RFfWqgQ


