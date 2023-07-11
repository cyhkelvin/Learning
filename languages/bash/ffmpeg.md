# ffmpeg

## commands
### transpose
 - `ffmpeg -i INPUT.mov -vf "transpose=1" OUTPUT.mov` [1:90度; 3:270度]
 - `ffmpeg -i input.mp4 -filter:v "transpose=1,transpose=1"` [180度]
### trim
 - `ffmpeg -i input.mp4 -ss 00:05:20 -t 00:10:00 -c:v copy -c:a copy output1.mp4`
 - `ffmpeg -i input.mp4 -ss 00:05:10 -to 00:15:30 -c:v copy -c:a copy output2.mp4`
### create gif from images
 - `ffmpeg -f image2 -framerate 1 -i simpimgs%03d.jpg -loop -1 simpimgs.gif`
    - `-i simpimgs%03d.jpg` – list of input images for the GIF file
    - `-framerate 1` means that FFmpeg will display each image for 1 second (frames/second).
    - `-loop -1` means that the GIF should not loop.
        - 0 = loop infinitely and this is the default value.
        - 1 = loop once (i.e. play two times)
        - 2 = loop two times (i.e. play thrice)
    - `simpson.gif` – name of the output file.
 - [reference for more examples](https://ottverse.com/how-to-create-gif-from-images-using-ffmpeg/)