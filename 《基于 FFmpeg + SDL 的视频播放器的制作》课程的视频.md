## 视音频基础知识 ##
H.264-解码->YUV格式后才能显示到界面上</br>
其中Y为亮度信息,UV为色度,浓度信息,YUV420P最常见</br>
人眼对亮度敏感而对色度不敏感,因而可以将亮度信息和色度信息分离</br>
Y Y Y Y      ---------------UV数据量是Y的数据量的一半</br>
Y Y Y Y</br>
U U</br>
V V</br>
YUV的表示法称为 A:B:C 表示法：</br>
4:4:4 表示完全取样。 4:2:2 表示 2:1 的水平取样，没有垂直下采样。 4:2:0 表示 2:1 的水平取样，2:1 的垂直下采样。 4:1:1 表示 4:1 的水平取样，没有垂直下采样。</br>

像素数据格式:RGB24,RGB32,YUV420P,YUV444P,YUV422P</br>
||R|G|B||R|G|B||  RGB依次存储每个像素点的R,G,B信息</br>
BMP文件较其他文件大很多

**音频采样数据体积很大**
4分钟:4 * 60 * 44100 * 2 * 2 = 43.3MByte</br>
44100为采样率,采样精度16bit</br>
**Adobe Audition**音频采样数据查看

人耳22.05kHz
双声道 L R L R .... L R</br>
MKV,MP4,AVI封装格式信息(Elecard Format Analyzer)</br>
H.264码流分析信息Elecara Stream Eye</br>
## FFmpeg命令行工具 ##
[http://www.cnblogs.com/dwdxdy/p/3240167.html](http://www.cnblogs.com/dwdxdy/p/3240167.html "命令行指令")</br>
ffmpeg.exe用于视频转码</br>
ffmpeg -i input.avi -b:v 640k output.ts</br>
-i:指定输入文件;-b:v设置视频码率;-t 5:视频时间5s;</br>
ffmpeg -ss 20 -i ..从20s开始截取</br>
-r 帧率</br>
-s 1280*720设置帧大小</br>
-c:v 设置视频编码器





