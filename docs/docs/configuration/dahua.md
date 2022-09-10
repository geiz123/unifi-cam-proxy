---
sidebar_position: 3
---

# Dahua/Lorex
### Options
```
optional arguments:
  --ffmpeg-args FFMPEG_ARGS, -f FFMPEG_ARGS
                        Transcoding args for `ffmpeg -i <src> <args> <dst>`
  --rtsp-transport {tcp,udp,http,udp_multicast}
                        RTSP transport protocol used by stream
  --username USERNAME, -u USERNAME
                        Camera username
  --password PASSWORD, -p PASSWORD
                        Camera password
  --channel CHANNEL, -c CHANNEL
                        Camera channel
  --snapshot-channel SNAPSHOT_CHANNEL
                        Snapshot channel
  --main-stream MAIN_STREAM
                        Main Stream subtype index
  --sub-stream SUB_STREAM
                        Sub Stream subtype index
  --motion-index MOTION_INDEX
                        VideoMotion event index
```

### Dahua N43AJ52
**Important:** You must set the camera video "Encode Mode" to `H.264` or you will get this error: `...hevc not compatible with flv`
```
unifi-cam-proxy -H {NVR IP} \
-i {camera IP} \
-c client.pem \
-t {Adoption token} \
dahua \
-u {username} -p {password} \
--c 1 \
--sub-stream 1 \
--snapshot-channel 1
```

### Lorex LNB4321B


- [x] Supports full time recording
- [x] Supports motion events
- [ ] Supports smart detection
```
unifi-cam-proxy --mac '{unique MAC}' -H {NVR IP} -i {camera IP} -c /client.pem -t {Adoption token} \
    dahua \
    -u {username} \
    -p {password} \
    --ffmpeg-args="-f lavfi -i anullsrc -c:v copy -ar 32000 -ac 1 -codec:a aac -b:a 32k"
```
