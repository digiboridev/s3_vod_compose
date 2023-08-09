# s3_vod_compose
Docker compose template for streaming video files from s3 and local storage with on-the-fly repackaging to HLS using kaltura's nginx vod module.
Uses minio as remote storage. 


## Building
```
docker compose build
```


## Running
```
docker compose up
```

* Nginx runs on port `3000`
* open port on server firewall
* Storage console address `http://console.localhost:3000/`
* For local stream, video files should be placed in `./videos` directory
* For remote stream, video files should be placed in `videos` bucked and have public read access



## Example URLs
* Base url: `http://localhost:3000`
* `/remote_thumb/<filename>` - thumb shortcut
* `/remote_thumb/<filename>/thumb-<time_ms>.jpg` - timed full
* `/remote_hls/<filename>` - hls shortcut for index.m3u8
* `/remote_hls/<filename>/<index.m3u8|master.m3u8>` - hls full
* `/vid/<filename>:thumb|hls` - shotcut for remote hls or thumb
* for local files, replace `remote` with `local` in the above urls



## Source
* [kaltura/nginx-vod-module](https://github.com/kaltura/nginx-vod-module)
