# Purpose

Enables professional-looking demo videos and screencasts like this to be made quickly using just Mountain Lion's in-built QuickTime.

# Instructions

- Install ffmpeg if you haven't already. If you have brew it's simply `brew install ffmpeg`
- Set the iPad simulator in "iPad" mode, portrait with the scale set to 100%
- Centre the iPad simulator (something like [BetterSnapTool](https://itunes.apple.com/gb/app/bettersnaptool/id417375580?mt=12) does this well)
- Load Quicktime and start a screen recording from the File menu
- When done, run the following command


```
ffmpeg -i INPUT.mov -qscale 0 -filter:v "crop=768:1024:(in_w-768)/2:(in_h-1024)/2+9" TMP1.mpg && ffmpeg -i TMP1.mpg -qscale 0 -filter:v "pad=968:1256:100:116:white" TMP2.mpg && ffmpeg -i TMP2.mpg -qscale 0 -vf "movie=ipad-overlay-gloss-no-shadow.png [watermark]; [in][watermark] overlay=0:0 [out]" OUTPUT.mpg
```



The command assumes the overlay and the INPUT.mov files are both in the same directory. Two TMP files are created - you can delete those. The quality settings need to be juggled with and are different across the many versions of ffmpeg you may uncover - see ffmpeg's manual



# Troubleshooting

I've not tested this on other hardware configurations, but it's possible alignment issues will occur. You can tweak this fairly easily by modifying the constants


# Credits

Without the amazing work of [teehan+lax](http://www.teehanlax.com) and their [iPad GUI PSD](http://www.teehanlax.com/tools/ipad/) this would have taken me much longer; the iPad screens are adapted from that file. Without Pixelmator, it would have cost more.


# Todo

- Permutations of gloss, no gloss and with and without shadow
- iPhone5 and iPhone4 in the above permuations
- Add landscape versions