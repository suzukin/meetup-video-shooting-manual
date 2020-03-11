# Meetup Video Shooting Manual

this is English Version docs, Japanese Version docs is [here](/manual-ja.md).

This document is linked with [Meetup video shooting Meetup(Japanese Version only)](https://mvsmjp.connpass.com/). We have released a manual to create a more comfortable viewing environment with our shooting know-how on live streaming and video archiving for Meetup.

0. Basic flow of live streaming
1. Check list with venue and speakers
2. How to use YouTube Live, Zoom, Teams, etc.
3. Mastering OBS (Open Broadcaster Software)
4. Appendix


## 0. Basic flow of live streaming (What do you want to do?)

summarizes the basic flow of live streaming for Meetup. In this document, online distribution, streaming, remote, etc. are collectively referred to as "**live streaming**", and virtual events and virtual conferences are collectively referred to as "**online events**". there are several patterns in the combination of live distribution / video archiving and events, but here we will proceed with the assumption that live distribution is involved.

Delivery format | With local participation | Without local participation
------------ | ------------- | -------------
Live streaming (+ archive video) | Offline event available | No offline event
Release the shot video later | Public recording | Studio recording

### 0.1. Live streaming with offline events

There is a limit to handling speakers, local participants and online participants alone, so it is necessary to decide on a role in advance. Probably the most difficult pattern. Prepare at least three people for each field. If the venue is not fixed, it is necessary to check the sound and network in advance. For more information, please refer to "Check list with venue and speakers".

- Moderator (for speakers)
- Venue (reception, guidance, etc.)
- Live streaming

TIPS: When a speaker participates remotely

### 0.2. Live streaming without offline events

Compared to the above, there is no need to care for local participants at the venue, so the load is somewhat reduced. Just focus on moderation and live streaming. However, the lack of local participants makes it difficult to get direct feedback on the presentation. Make sure that people in the same place (such as moderators and other speakers) do reactions such as applause and hammering. please refer to "Facilitate feedback from remote participants".

TIPS: Facilitate feedback from remote participants<br>
Twitter TL, Chat Box, Slido, Mentimeter, etc.

### 0.3. Other formats

Although we will not go into detail here, there are also public recording patterns that leave videos as archives with emphasis on offline events with local participation, and studio recording patterns that emphasize video archives such as webinars.

Summary. If live streaming is a prerequisite, consider whether there are local participants, and whether all speakers will gather at the venue or allow remotes. Alternatively, determine how much effort you will spend on live streaming for offline events that take place locally.


## 1. Check list with venue and speakers

We recommend that you check the following items in advance if you decide to broadcast live. It is important to note that when running with an offline event, the audio and the network must care for both local participants and live participants.

### 1.1. Sound equipment (PA)

- Audio output connector
  - XLR
  - Phone（3.5mm mini、6.3mm basic）
  - RCA（red/whitle pin cable）
  - USB
- Number and type of microphones
  - Wired
  - Wireless (Hand, Pin)
  - Other type (such as conference rooms)

※ [PAビギナーズガイド | トレーニング＆サポート | ヤマハプロオーディオ(Japanese Version only)](https://jp.yamaha.com/products/contents/proaudio/musicianspa/equipments/cable.html)<br>
* Be careful not to confuse with the audio input cable on the podium. In many cases, a PA rack containing a mixer etc. is available. Be careful as the racks are often locked! <br>
* A conversion connector for the above cable is required to capture the audio output to the distribution PC.

### 1.2. Network environment

- Wired or Wireless-Fi）
- Port number

* Regarding Wi-Fi, it is necessary to refuse visitors or separate lines to secure stable bandwidth of distribution PC <br>
* Check if there is a LAN cable port on the distribution PC <br>
* Please note that depending on the venue, the port numbers that can be used are limited and distribution (basically 80: HTTP) and demonstrations may not be possible!


## 2. How to use YouTube Live, Zoom, Teams, etc.

In conjunction with the YouTuber boom, many online distributions use YouTube Live. Microsoft Japan also operates a YouTube channel for developers called "[クラウドデベロッパーちゃんねる](https://www.youtube.com/channel/UCMmRHq3E_9Hc9noZeo3zDCw)" (currently, it is not used for online distribution but edited and published in studio shot videos). YouTube can be used for free with a Google account, and editing and publishing of videos can be completed on the browser. Videos delivered online are archived on YouTube as they are, so if you make simple edits such as setting titles, thumbnail images, and descriptions, you can immediately publish them on the channel.

There are other ways to take advantage of online conferencing platforms such as Teams and Zoom. For example, "[What are Microsoft Teams live events?](https://aka.ms/AA7jo0v)" can distribute content to up to 10,000 people. Depending on the setting, all participants can speak and make presentations using screen sharing, so it is attractive to be able to speak from a remote location anywhere and participate in discussions interactively.

For distribution of YouTube Live, Teams, Zoom, etc., recording is usually performed using the built-in camera and built-in microphone of the personal computer. However, in order to live stream a Meetup, you need to work with a variety of sources. For example, you want to capture the slides, show the speakers with the camera, the speakers are remotely located, record the sound of the event venue, and want to display the Twitter timeline because you want to know the reactions of the participants. Such a request comes out. In order to solve these problems, we are using a combination of streaming software such as "OBS Studio" and equipment called a mixer / switcher. Let's introduce them in order.

### 2.1. Necessary equipment

- Speaker PC
  - It is common to capture by HDMI, but it is safe to prepare an RGB connector because HDMI digital signal attenuates and often causes problems due to compatibility problems such as hubs and protection
  - If you are speach remotely, sound is very important so you should be able to pick up sound properly, in some cases please prepare a headset or USB microphone
- Delivery PC
  - We strongly recommend models (eg, gaming PCs)  that emphasize performance over design and portabilityas they become the cornerstone of distribution. External GPU is required to handle video
- Camera
  - A separate camera is also required if you want to shoot the speakers at the venue and distribute the footage, so fix it with a tripod. The connector count differs depending on the product, but it is common to end up with HDMI to the switcher or distribution PC in the end

The list of equipment actually used in Daikanyama and Shinagawa is up for reference.

### 2.2. Delivery method

- YouTube Live

Here, we will explain the flow of creating a video for distribution using the general [OBS (Open Broadcaster Software)](https://obsproject.com/en) and live broadcasting on YouTube Live. The video and audio of the speakers will be sent to the PC for distribution via Zoom. The PC for distribution can also be used as the speaker's PC, but it is recommended that you prepare another machine if possible.

- OBS: There is a setting for YouTube distribution so use it, Can be set in a wizard from the app.
- YouTube Live: Complete the operation on the browser. Select the encoder distribution, pass the "stream key" information issued on the management screen to OBS

```
POINT

To broadcast live on YouTube, you need to wait up to 24 hours to activate the settings after creating a channel.
We also recommend using a brand account to collaborate on your channel (managed by multiple Google accounts).
[YouTube Help: Enable Live Streaming](https://support.google.com/youtube/answer/9227509?hl=en)
[YouTube Help: Manage YouTube channels](https://support.google.com/youtube/answer/4642409?hl=en)
```

Once you have connected to Zoom from the distribution PC and confirmed the speaker's screen and audio, select Zoom as the input source on the OBS side. When you're ready, start streaming OBS (you haven't started streaming YouTube yet). Next, open the YouTube setting screen on the browser side and check whether the data from OBS has been imported. Click the YouTube live streaming button to start streaming.

- Zoom, Teams, Skype, etc

For online meetings such as Zoom, a paid account may be required. Check the specifications, such as the time available for delivery and the number of simultaneous connections, and select an appropriate service. You should check the manuals and web articles of each service for usage. Here, we will explain how to distribute the Zoom screen on YouTube Live by taking Zoom as an example of an online event. Install the Zoom client application on each speaker's PC. Projection is possible from a web browser, but the standalone application is more stable. Master three basic steps: audio, video, and share screen.

- audio: Controls the PC's built-in microphone or an external microphone connected via USB or earphone jack
- video: Control the built-in camera of PC or external camera as well as microphone
- share screen: Select a window to share the screen, be aware that presenter tools may be screen-shared when in presentation mode

### 2.3. When a speaker participates remotely

By using Zoom and Teams, you will be able to speak remotely. In particular, speakers are encouraged to participate in conference rooms with quiet surroundings and a stable network. Shooting in a studio or in a familiar space is recommended because the distribution equipment is easy and the setup is easy. Meetups where the venue changes every time are often troublesome and previewing is strongly recommended. The most important confirmation points are **the audio equipment (PA)** and **network environment** mentioned in the coordination list with the venue and speakers.

### 2.4. Facilitate feedback from remote participants


## 3. Mastering OBS (Open Broadcaster Software)

### 3.1. Handle multiple input sources

Centrally manage multiple input sources, such as live broadcast of offline events, such as projecting the screen of the speaker's PC on the projector of the venue, shooting the speaker's figure with the camera, projecting the screen of Twitter and other tools I think there are many scenes that I want to distribute. All the "pictures" to be finally distributed live can be managed by OBS, but a device called a switcher is required to physically import those sources into a distribution PC. I use "[ATEM Mini](https://www.blackmagicdesign.com/jp/products/atemmini)".


In the past several meet-ups, there were almost twice as many remote participants as actual results. There are many people who are participating from the local area and many who are unable to go to the venue in a hurry due to work, so there is definitely a need for online distribution. Why don't you consider online distribution for the event you are in charge of?


## 4. Appendix

### 4.1. Configuration diagram of distribution equipment and network (TBD)

composition diagram is under construction, the following two patterns are relatively simple and very helpful.（thx! ＠goofmint, @kojikita）

- [リモート/オンラインで勉強会をやる際によさそうなテクニック(Japanese Version only)](https://devrel.jp/%E5%8B%89%E5%BC%B7%E4%BC%9A/%E3%82%A4%E3%83%99%E3%83%B3%E3%83%88/2020/02/20/online-meetup.html)
- [ミクシィグループの勉強会生放送事情を紹介します！ その２(Japanese Version only)](https://medium.com/mixi-developers/live-system-2-967c56396b69)

### 4.2. Reference

- [オンラインイベント開催のガイドライン(Japanese Version only)](https://blog.granica.io/etc/70/)
- [オンラインイベントを実施する上で私は何を考えどう行動したか①（+参考になる記事まとめ）(Japanese Version only)](https://medium.com/@szkn27/onlineevent-howto-c8a9f6af214b)
- [Meetup video shooting Meetup(Japanese Version only)](https://mvsmjp.connpass.com/)