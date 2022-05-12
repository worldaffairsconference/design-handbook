# Livestream

The livestream is a relatively new portion of WAC that was started in WAC 2018, where [we livestreamed Professor Geoffrey Hinton's Keynote Address to Facebook](https://www.facebook.com/worldaffairsconference/videos/1534897316578312/) \(as well as some of the programs during the day\). Livestreaming is a very important tool - it broadens the accessibility of WAC, especially to those who don't live in Toronto. While it seems daunting, setting up the livestream is actually relatively simple - it just has a lot of moving parts. No prior technical skills are required, though familiarity with livestreaming and design are recommended.

## The Technology Stack

There are three layers of technology at work in the livestream: the input layer, where input audio and video is captured, the processing layer, where audio and video is processed for output, and the output layer, where the video is uploaded to a streaming service and shown to the public. In practice, one or two people can manage the entire livestream, including all three of these layers. Let's break it down at each step.

## Input Layer

The input layer is the capturing of any live audio and video. Typically, this is accomplished with a camera, a microphone, and tapping into a sound system \(e.g. Laidlaw Hall\). The inputs are then fed to the processing layer, with added visual aids and sound effects.

### Equipment

While there aren't any exact peripherals required to create the input layer, WAC \(and UCC\) already has infrastructure for the input layer, so we recommend that you start from there.

| Item Type | Example Item | Item Description | Where to get |
| :--- | :--- | :--- | :--- |
| Camera | Canon EOS 5DS | This camera is the input video feed. For whatever camera used, ensure that there are sufficient batteries and that the camera can film video for as long as needed. | UCC Film Dept. |
| Tripod | Tripod | A tripod should be used for a static shot \(e.g. one of Laidlaw Hall\). | UCC Film Dept. |
| Video Interface\* | Canon EOS Utility + Camera Live | Converts input feed from the camera into digital video sent to the computer. | [EOS Utility](https://www.usa.canon.com/internet/portal/us/home/support/details/cameras/dslr/eos-5ds), [Camera Live](https://github.com/v002/v002-Camera-Live) |
| Audio Interface | Audient iD14 | Collects all input audio \(e.g. line in from Laidlaw Hall Booth, line in from microphone, other computers\) into one digital signal sent to a computer. | UCC Film Dept. |



### Notes

Most of the work for the input layer is just setup work - go to the venue an hour or so in advance, set up the tripod, focus the camera, and connect the audio interface to the audio source\(s\). During the actual event, if everything is set up properly, the only action that needs to be done is to check on the camera's battery.

Setting up the video interface is the most complicated part of input layer, as it's relatively unreliable software-wise. Use the EOS Utility and its drivers to preview the video feed from the camera, and then use Camera Live to create a Syphon server that the processing layer can tap into. If you use a non-Canon camera, we don't have a tested solution for you - beware!

## Processing Layer

The processing layer's job is to take these inputs and stitch them together with other visuals to create an uploadable final product. The entire processing layer is software-based and happens on one computer, which makes things both convenient and hectic. However, with experience, it becomes very simple.

The central hub for the processing layer is the broadcasting software. We highly recommend using [Open Broadcaster Software \(OBS\)](https://obsproject.com/), a production-ready open-source broadcasting software that's used by professional streamers and by our livestreaming crew. OBS is pretty intuitive to use, and our use case is rather light, but if you want to familiarize yourself with the software the internet has a plethora of resources on using and configuring it.

Since the processing layer is the most skill-intensive part of the livestream, **we strongly recommend that you do a practice run of the livestream** - it can spot problems that are likely to happen during the livestream and familiarizes the software with you.

### Video Source

_This section will assume that you're using a Canon camera + EOS Utility + Camera Live with OBS on a Mac running OSX. There are other ways to do this on different platforms, but they are untested._

Here's a step-by-step guide to creating an OBS Video Source of the camera feed.

1. Connect the camera to your computer via USB.
2. Open up EOS Utility, and preview the video feed.
   * If the preview fails, try re-installing EOS Utility and its drivers.
3. Open up Camera Live, and select your connected camera.
   * If Camera Live doesn't recognize any cameras, close everything and start again.
   * If Camera Live errors, try restarting it and/or EOS Utility.
4. In OBS, create a new Game Capture/Syphon source, with Camera Live's Syphon process as the input source.
5. The newly-created source should now be usable in any scenes.

The video source is by far the most unreliable and frustrating part of the livestreaming process, so be patient. 

### Audio Source

Creating different audio inputs for OBS is quite simple - just add an Audio Source through the OBS menu, and make sure that your levels are managed!

A quick note on music: most streaming services, such as Twitch and Facebook, will mute parts of your content for containing copyrighted music. We recommend muting any music sources in OBS, or else parts of the video will be muted.

### Secondary Visual Content

Often times, presenters will have additional A/V needs \(e.g. a video or audio\). There are three different ways that you can put this content into the livestream:

* Pan the camera to the A/V content, and tap into the audio through the audio interface is needed.
* Take a digital line in of the A/V content from its source \(e.g. the Laidlaw Hall computer\)
* Create a copy of the A/V content on the processing computer, and then use a Window Capture source to listen in on the content.

### Tips and Tricks

There are simple things that you can do to make the stream better:

* Add visual information \(in the form of images\), such as our logo, social media, programs
* Use multiple scenes with different presets and transitions to smoothly switch between different types of content \(e.g. going from a close-up to a wide shot of the entire room\)
* Before and after the stream, show content instead of an empty podium \(i.e. the WAC Video\)
* Monitor the output audio with headphones - it's important to know what the stream will sound like.

### Sample Stream Schedule

Here's what a stream schedule would look like for the keynote event.

| Time | Stream Action |
| :--- | :--- |
| ~ 15 minutes before event start | Turn on stream, project a still image of WAC and our speaker's topic and/or a video of the venue, and play non-copyrighted music |
| ~ 3 minutes before event start | Transition to WAC Video on stream |
| Keynote start | Transition to close-up of podium, key in podium audio with audio interface |
| Introduction of speaker | Zoom out and pan to speaker going to podium, mute podium audio |
| Speaker start | Transition to two-visual setup \(both the speaker's slides and a video of the speaker on the podium\), key in podium audio |
| Q&A Session | Zoom out and pan to general view of venue, key in Q&A microphone audio |
| Thanking speaker | Zoom out and pan to the venue |
| End of event | Project still image with program details of tomorrow's event, play non-copyrighted music |



## Output Layer

After the processing layer has done its work, there is now one completed video and audio stream that is ready to be shown to the public. The output layer uploads this video stream to the respective streaming service \(e.g. Facebook, Twitter/Periscope, YouTube\).

Generally, this step is pretty easy \(as each video stream vendor will have instructions on how to configure OBS to output to their stream\). Typically, it involves creating a stream key on the vendor's site, inputting that into OBS' "Stream" menu, and selecting the correct service to stream.

For WAC 2018, we streamed to Facebook Live simply due to ease of access, but video can be streamed to many different services. Here are some links that explain how to send the output to various vendors:

* Facebook Live \([Tutorial from FB Live](https://www.facebook.com/help/publisher/167417030499767?helpref=page_content), [Tutorial from OBS](https://obsproject.com/forum/resources/how-to-stream-to-facebook-live.391/)\) \(make sure to use the WAC FB Page\)
* Youtube \([Tutorial from Youtube](https://support.google.com/youtube/answer/2474026?hl=en)\)
* Twitter/Periscope \([Tutorial from Periscope](https://help.pscp.tv/customer/en/portal/articles/2600293-what-is-periscope-producer)\)



