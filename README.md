# Media Player Jukebox for Home-Assistant

This is a media player UI for Home-Assistant leveraging the potential of the excellent new
[Lovelace UI.](https://www.home-assistant.io/lovelace/)

It allows you to configure a set of web radio stations (or possibly other radio media IDs such as spotify), and
play them to media player entities of your choice, like chromecast or spotify connect listeners.

You can send different media to different players, which makes it usable for multi-room setups: Let your kids listen
to some *Frozen*, while you're Jazzing in the Kitchen. Volume-Level is handled separately, too.

## Screenshot
![alt text](https://github.com/lukx/home-assistant-jukebox/blob/master/screenshot.png?raw=true "See the jukebox in action")

## Acknowledgement
Apart from the home-assistant project, I need to say thanks to User [Bob_NL](https://community.home-assistant.io/u/Bob_NL)
who made his evergreen [Chromecast Radio](https://community.home-assistant.io/t/chromecast-radio-with-station-and-player-selection/12732)
available to all of us in the Home-Assistant forums. This jukebox is heavily deriving from the great work of all the
people in the thread.

## Usage
### Preparation
This will take time, but do set up your home-assistant to use the new [Lovelace](https://www.home-assistant.io/lovelace/)
frontend, if you're not using it yet.

### Installation
Grab a copy of [jukebox.js](./jukebox.js) and save it into your home-assistant's configuration, in a folder called
"www". So:

```
- /.homeassistant
|___ /configuration.yaml
|___ /www/jukebox.js
```


### Configuration
Find stream URLs, e.g. on [Radio-Browser.info](http://www.radio-browser.info/gui/#/)
See this example setting a couple of Web radios to my two chromecast players.

*Excerpt of ui-lovelace.yaml*
```
resources:
  - url: /local/jukebox.js
    type: module
views:
- name: Example
  cards:
  - type: "custom:jukebox-card"
    links:
      - url: http://streams.greenhost.nl:8080/jazz
        name: Concertzender Jazz
      - url: http://fs-insidejazz.fast-serv.com:8282/;stream.nsv
        name: Inside Jazz
      - url: http://stream.srg-ssr.ch/m/rsj/mp3_128
        name: Radio Swiss Jazz
      - url: http://stream.beachlatinoradio.com:8030/;?d=
        name: Beach Latino Radio
      - url: http://streams.calmradio.com/api/43/128/stream/;?d=
        name: Calm Radio
      - url: http://swr-swr1-bw.cast.addradio.de/swr/swr1/bw/mp3/128/stream.mp3
        name: SWR 1
      - url: http://94.23.252.14:8067/stream
        name: Nature Sounds
    entities:
      - media_player.wuerfel_wohnzimmer
      - media_player.wuerfel_kueche
```
