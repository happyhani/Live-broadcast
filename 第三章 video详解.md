<video id="video-container-mocoplayer-hls-video_html5_api" class="vjs-tech" preload="auto" autobuffer="" src="blob:https://coding.imooc.com/770b5b37-a721-42ad-97f6-3ba9f3e937af"> </video>
慕课网的视频连接，blob:https://coding.imooc.com/770b5b37-a721-42ad-97f6-3ba9f3e937af是一个虚拟地址，所以无法下载。video可以src一个虚拟地址

####  3-2 准备工作

腾讯视频上下载，新的视频电视剧是hls格式的，虚拟地址下载不下来，可以下载老的视频是mp4格式的。

需要装一个Chrome插件

####  3-5 video属性和方法（3）
场景一：当网络问题，或CDN不稳定，一时无法获取到新视频的地址该如何处理，获取一个备用地址去正常播放？
  source引用同一个视频，视频放在不同的域下，当第一个域出错的时候回启动另一个域
场景二：监控，监测到错误再上报回去，例如第一个视频播放失败，把错误的地址上传？
 video.currentSrc之前的都是错误的

 ####  3-6 video事件（1）
 视频查找loadstart
 时长变化：video初始化的时候duration是NaN ，当他加载完之后拿到视频信息长度的时候会触发durationchange。变化的时候不一定会一次获取整个视频时长。durationchange不一定触发一次，有可能2次或多次
 元数据加载loadedmetadata
 视频下载监听loadeddata：没有可播放的视频时，继续下载 执行progress去下载足够的视频帧和音频帧
 可播放监听canplay：有帧可以播放，流畅播放canplaythrough
 播放监听play
 暂停监听pause
 查找开始seeking
 查找结束seeked：查找完毕可以播放，单击的瞬间先触发seeking
 视频加载等待：无法解码，视频画面无法改变的时候，有播放状态到暂停状态的时候。
 playing：没有播放->播放会触发playing
 视频结束ended
 error：例如断网时，浏览器会自动重刷31次后，执行error事件