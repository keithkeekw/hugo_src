---
title: "Manage Youtube Channels with Newsboat and mpv"
date: 2020-12-25T22:38:56+08:00
draft: false 
tags: [linux]
---
## Objectives:
1. To manage all my favourite YouTube Channels as well as newsfeed.
2. To avoid all the ads from Youtube.

## Softwares Required
- [mpv](https://mpv.io/): A minimal video player for terminal console.
- [newsboat](https://newsboat.org/): RSS Reader for terminal console.

## Setup for newsboat
1. After the installation, proceed to create `.newsboat` folder in your home directory.
    ```
    mkdir .newsboat
    ```
2. Next, proceed to create 2 files which are `config` and `urls`.  
  - `config`: All the configuration for the newsboat will be placed in this file.  
  - `urls`: RSS URLs will be stored in this file. 
  
    ```
        keithkeekw@1983 ~/.newsboat                                                      [21:58:42] 
      > $ tree                                                                                   
      .
      ├── config
      └── urls

    ```

3. In the `config` file, proceed to populate the necessary settings. Refer to the [official documentation](https://newsboat.org/releases/2.22/docs/newsboat.html#_example_configuration) for further information. Below is my configuration:
    ```
    auto-reload yes
    reload-threads 100
    macro m set browser "/usr/bin/mpv -fs %u"; open-in-browser ; set browser "/usr/bin/firefox %u"
    macro b set browser "/usr/bin/qutebrowser %u"; open-in-browser ; set browser "/usr/bin/firefox %u"

    bind-key k up
    bind-key j down
    bind-key h prev
    bind-key l next
    bind-key c cmdline

    color info        black   yellow    bold
    color listfocus   white   blue      

    ```
    The most important setting for this setup is:  
    - `marco m set browser "/usr/bin/mpv -fs %u"; open-in-browser ; set browser "/usr/bin/firefox %u"`

4. Next, proceed to populate the Youtube channels RSS as well as other newsfeed RSS into the `urls` file. Below is the content for my file:
    ```
    https://www.youtube.com/feeds/videos.xml?channel_id=UCVls1GmFKf6WlTraIb_IaJg "~[YT-Linux] Distrotube"
    https://www.youtube.com/feeds/videos.xml?channel_id=UCX_WM2O-X96URC5n66G-hvw "~[YT-Linux] EF - Tech Made Simple"
    https://www.youtube.com/feeds/videos.xml?channel_id=UCld68syR8Wi-GY_n4CaoJGA "~[YT-Linux] Brodie Robertson"
    https://www.youtube.com/feeds/videos.xml?channel_id=UCOCDkCdOB-Ca4PF4jHU3Ksg "~[YT-Auto] Chris Wee"
    https://www.youtube.com/feeds/videos.xml?channel_id=UCL6JmiMXKoXS6bpP1D3bk8g "~[YT-Auto] Donut Media"
    https://www.youtube.com/feeds/videos.xml?channel_id=UCes1EvRjcKU4sY_UEavndBw "~[YT-Auto] ChrisFix"
    https://www.youtube.com/feeds/videos.xml?channel_id=UCUQo7nzH1sXVpzL92VesANw "~[YT-DIY] DIY Perks"
    https://www.youtube.com/feeds/videos.xml?channel_id=UC7w0q4MgYxrYLcZqtScOcMw "~[YT-Entertainment] Neyna Story"
    https://www.youtube.com/feeds/videos.xml?channel_id=UCoC47do520os_4DBMEFGg4A "~[YT-Entertainment] Liziqi"
    https://www.youtube.com/feeds/videos.xml?channel_id=UCMG7DKIrpZoJlRLqYe9NtQg "~[YT-Entertainment] JinnyBoyTV"
    https://www.youtube.com/feeds/videos.xml?channel_id=UC8az0OO4wXXu2k0ifJjxxBg "~[YT-Entertainment] NOC"
    https://www.youtube.com/feeds/videos.xml?channel_id=UCFRIAxGTWQ4mllzdkdomAkQ "~[YT-Entertainment] Team NOC"
    https://linuxize.com/index.xml "~[Article-Linux] Linuxize.com"
    https://flathub.org/api/v1/apps/collection/recently-updated/feed "~[Article-Linux] Flathub - New & Updated Apps"
    http://feeds.feedburner.com/NirAndFar "~[Article-Productivity] Nir and Far"
    https://www.omgubuntu.co.uk/feed "~[Article-Linux] OMG! Ubuntu"

    ```
5. In order to get the RSS for Youtube channel, you need to get the unique ID from the URL. For example, https://www.youtube.com/channel/UCld68syR8Wi-GY_n4CaoJGA where it's unique ID is `UCld68syR8Wi-GY_n4CaoJGA`. You need to populate the unique ID into the following template:  
    ```
    https://www.youtube.com/feeds/videos.xml?channel_id={unique ID}
    ```
## How to use it
1. Launch `newsboat` from your favourite terminal emulator and the application will proceed to grab all the latest updates from the site.
2. Go into the Youtube channel via the `newsboat` and it will list out videos which is available.
3. Activate the macro with `,` + `m` and mpv player will grab the url and play it out.
  
### Resources
- [Newsboat RSS Reader - Not Just For News Feeds by DistroTube](https://www.youtube.com/watch?v=CJXdQTGm1jg)
