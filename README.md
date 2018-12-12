# videosplitter
Windows program that runs video files from certain cctv systems through ffmpeg, outputting something more practical. 

The programs main purpose is to split video files from cctv systems, where video from several cameras are multiplexed into a multi streamed video file. Each output file is then supposed to have video, and hopefully its subtext, from one single camera. 

The reason for this, is that unless the recipient of the video file is aware of the multi stream nature of the video file, they may think the video file only contains the video from the first stream. Additionally, some video playback software will automatically open several playback windows. Each window playing back one video stream. This may be annoying to the recipient of the video file. Having the streams in separate files will be more practical anyway. 

The default behavior of the program is to be foolproof. It does not destroy the input file. It does not reencode the video stream. All it does, is to multiplex the first video stream, with the first subtext stream, and the first audio stream. It then multiplex the second video stream with the second subtext stream, and the second audio stream. And so on. If several files are chosen as input, each output file will only contain streams from one single input stream.

Output files will have the same name as the input file, with "_stream_[stream number]" added before the file extension. This should avoid most dangers of overwriting. But any files with the same file name as the output file, will be overwritten silently. All output files are saved in the same folder as the input files. Because of the danger of overwriting, you should keep a backup folder with the original files, and copy those to a work folder, for splitting. So don’t work directly on the only copies you have. 

I have added options to the ffmpeg command line, that attempts to repair the stream/file. The users may therefore use the program to attempt to repair video files that appear damaged. It does not reencode the streams, as stated above. It only tries to rebuild the timing and build an index. This way a damaged file may play back more reliably in most players. But the stream will still be damaged. 

It is important to know that the output file will only contain one video, subtitle and audio stream. By inputting a video file with one video stream, three subtitle streams and two audio streams, you will get an output file with the first of each stream type. There will be built no files for the remaining subtitle and audio streams. But if an input file contains five video streams, and no subtitle or audio streams, you will get five output files, with one video stream in each. 

The program only outputs matroska (.mkv) files. If you need something more advanced, like device compatible .mp4 files, you will be better helped with ffmpeg, avidemux and stuff like that.
