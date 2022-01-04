### 读取视频帧信息
`ffprobe -show_frames -select_streams v -of json input >> frames_info.txt`
命令解释：
* show_frames: 获取帧信息
* select_streams v: 仅读取视频流
* -of json: 以 JSON 格式输出
* `>>` : 重定向到文本文件，因为视频帧信息很多，控制台不方便查看

结果示例：
```
{
            "media_type": "video",
            "stream_index": 0,
            "key_frame": 1,
            "pkt_pts": 3000,
            "pkt_pts_time": "0.033333",
            "pkt_dts": 3000,
            "pkt_dts_time": "0.033333",
            "best_effort_timestamp": 3000,
            "best_effort_timestamp_time": "0.033333",
            "pkt_duration": 3000,
            "pkt_duration_time": "0.033333",
            "pkt_pos": "156877",
            "pkt_size": "152553",
            "width": 720,
            "height": 1280,
            "pix_fmt": "yuv420p",
            "sample_aspect_ratio": "1:1",
            "pict_type": "I",
            "coded_picture_number": 0,
            "display_picture_number": 0,
            "interlaced_frame": 0,
            "top_field_first": 0,
            "repeat_pict": 0,
            "chroma_location": "left"
        }
```
重要信息解释：
* stream_index: 流索引
* key_frame: 是否是关键帧
* pkt_pts: 帧的 pts 值 （Presentation Time Stamp，显示时间戳）
* pkt_pts_time: 通过 time_base 计算出来的实际显示时间
* pkt_dts: 帧的 dts 值（Decoding Time Stamp， 解码时间戳）
* pkt_dts_time: 通过 time_base 计算出来的实际解码时间
* pkt_duration: 帧持续时长
