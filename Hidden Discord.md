# About
**Category**: Misc
**Question**: Hidden Discord
**Flag**: RWSC{r34d_d15c0rd_d3v3l0p3r_API_r3f3r3nc3}

**Description**
In thise question we were ask to join a hidden discord and find the seperated flag in the discord server.

# How to Solve?
When we joined the server we will saw a welcome message showing with the given infomation the flag were seperated into `5 parts`.  

I started to navigate around the channels and we will see the flag segment for `Part 3 : d3v3l0p3r_`in the Event.

![enter image description here](https://media.discordapp.net/attachments/1156219870975897671/1214973519830589470/image.png?ex=65fb0f44&is=65e89a44&hm=d2abfb5505fdbd322d957c55fa3a5ec97944e50e44cdde477d4c10b92693363b&=&format=webp&quality=lossless&width=965&height=601)

Then, we check on the voice channel named first as I was suspecting the first part of the flag is there, when we click into the chatroom of the voice channel we will see the flag for `Part 1:RWSC{r34d_`

![enter image description here](https://media.discordapp.net/attachments/1156219870975897671/1214974063286681600/image.png?ex=65fb0fc5&is=65e89ac5&hm=8be8226900e449e451fab837bf1d43b7eed5fed2f58a562304946643f08ed38f&=&format=webp&quality=lossless&width=651&height=488)

Next with the hint provided at the hints channel we can see the admin with hidden role tag says tools and script are allow for this challenege. Hence I was suspecting there might be hidden channel. In order to view the hidden channel we need to download 
`BetterDiscord` (https://betterdiscord.app/)
 and insert the ShowHiddenPlug in from (https://github.com/JustOptimize/return-ShowHiddenChannels) to BetterDiscord, for details can check on https://youtu.be/_tyX9xzKfzc.

Then we can see the hidden category named `Part 4:API_`  that is the fourth segment of the flag. When we clicked into the channel named `dont_tell_other_about_server_icon` we can see there is a the flag for `Part 2: d15c0rd_`.

![enter image description here](https://media.discordapp.net/attachments/1156219870975897671/1214977342129311754/image.png?ex=65fb12d3&is=65e89dd3&hm=832a1b3897b162d100b2e7f9b8a54aef17b484556d913f83586a8ae945615a11&=&format=webp&quality=lossless&width=1237&height=436)

The channel `dont_tell_other_about_server_icon` was also the hint, I use inspect mode to check on the server icon picture and the final flag `Part 5:r3f3r3nc3}`found.

![enter image description here](![image](https://github.com/hiroyuki01233/RentasCTF-FreshHacker/assets/145642080/6b86388a-4a3c-460b-8fb7-64528539a0c9)
)

Lastly, we only need to combine all the flag segment accordingly 

> Part 1:RWSC{r34d_ 
> Part 2: d15c0rd_ 
> Part 3 : d3v3l0p3r_ 
> Part 4:API_
> Part 5:r3f3r3nc3}

and we will get our final flag `RWSC{r34d_d15c0rd_d3v3l0p3r_API_r3f3r3nc3}`

