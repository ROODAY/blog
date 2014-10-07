---
layout: post
title: "LexHack: A Cautionary Tale of Ambition"
date: 2014-10-05 22:09:15 -0400
comments: true
sharing: true
footer: true
categories: 
- Programming
- Hackathons
---

&nbsp;&nbsp;&nbsp;&nbsp;Hackathons. Making the best program/application that you possibly can in a short span of time. Sounds like a perfect way to spend a day, doesn't it? In all honesty, hackathons are quite fun, especially if you know what you're doing, but even just to see the cool things that other people create. On Saturday, September 27th, was the first LexHack, a hackathon hosted at Lexington High School for programmers of all levels. Coincidentally, it was also my first hackathon experience.

<!--more-->

{% http://i.imgur.com/kbRUDxJ.jpg 400 400 LexHack %}

&nbsp;&nbsp;&nbsp;&nbsp;Before heading into the event, I made a group with some friends of mine, called [WWPOL](https://github.com/WWPOL), as going solo would be an unnecessarily hard challenge for my first time. We had already worked together on a project for the JS13k competition the previous month, called [Earth Invader](https://github.com/WWPOL/Earth-Invader). (We placed 88th out of 129, but we're still proud of the game itself) Once we figured out which of us were able to attend LexHack, we set out on thinking of an idea so that we wouldn't enter unprepared.

{% https://raw.githubusercontent.com/WWPOL/Earth-Invader/gh-pages/screenshots/3.png 640 360 Earth Invader %}

&nbsp;&nbsp;&nbsp;&nbsp;We quickly settled on the idea of making a turn based, online, two player battleship game using [Phaser.js](http://phaser.io/) and [Socket.io](http://socket.io/), called [RTShips](https://github.com/WWPOL/RTShips). At first, it seemed like a great idea. We'd use Phaser to do all the rendering and dealing with sprites, which would free up our time to worry with the more important things like synchronization and game logic. And for synchronization, we'd be able to use Socket.io to deal with sending turn data to each player, so we'd really only have to spend time on the game itself. Or so we thought.

&nbsp;&nbsp;&nbsp;&nbsp;As the day drew nearer, we began thinking of more and more features that we could add that would make the game look more impressive, such as a fog of war style UI, inspired by the Civilization games, and a targetting overlay for battleships to use when firing. Although we eventually got around to dealing with implementation, we had done too much what, and not enough how. The night before, we made our final checks on the idea, and I drew up sprites, as textures were allowed to be made beforehand. (And [they](https://github.com/WWPOL/RTShips/tree/master/public/assets/ships) weren't too bad, if I do say so myself) After that, all we could do was wait.

&nbsp;&nbsp;&nbsp;&nbsp;When I arrived at Lexington High School (with a fair bit of diffculty as my GPS led me to the back of the school for some odd reason), I was happily surprised at the turnout. It wasn't too big a group, as that would mean too much competition, but it wasn't so low to the point where it wouldn't be fun. (The actual number was pretty close to 80) The only issue was that our group was originally five people, but about a week before two of them had to cancel, leaving us shorthanded. Othat than that note, nothing really interesting happened in the registration/preparation period, other than a member of my team bringing munchkins. Thanks Phil! At about 9:30 in the morning, the hacking began, and WWPOL furiously set to work.

&nbsp;&nbsp;&nbsp;&nbsp;Initially, RTShips was going pretty swell. We quickly got some sprites up on the screen, and within the hour we had implemented a large map that a player could scroll around. After a couple hours or so we had the ability to move sprites by clicking on them, then clicking on a tile for them to move to. But, at about 4-5 hours, the troubles began.

&nbsp;&nbsp;&nbsp;&nbsp;Firstly, we had trouble moving more than one ship. Any good turn based strategy game would allow the manipulation of more than one unit, correct? Well, RTShips was lacking in that aspect. The game had an issue where after you clicked one ship, you could no longer select another ship. Clicking anywhere else around the board would just move the original ship. Not so good... Many more minor problems ensued, namely features like scrolling or clicking certain buttons breaking, but the biggest issue occured at about half way through the hackathon, where we had an entirely game breaking error that was connected to a fundamental part of the game: sending data to the other player.

&nbsp;&nbsp;&nbsp;&nbsp;Socket.io was designed for small packets of data, like strings of text for a [chatroom](https://github.com/philsiff/ChatAnon), for example. One thing we didn't realize going in, as we honestly didn't have enough experience with Phaser.js, was that Phaser's sprites were really, *really* large objects, with many different properties. Trying to send even one Phaser sprite through a socket hook would break socket, and this issue stalled our progress for a solid thirty minutes. In the end, we didn't ever get past the issue, as we ditched RTShips, and all three of us split off into making separate projects. One used the RTShips sprites to make a whack-a-mole-esque game which used socket multiplayer, another attempted to continue working on the game without Phaser, and I tried to make a two player pong using socket. 

&nbsp;&nbsp;&nbsp;&nbsp;Fast forward another 5 or so hours, and there's barely any progress, except for the whack-a-mole game. During one of our deep, reflective breaks, we realized that we had endured the five stages of grief during our failed development of RTShips, and we all laughed it off and basically said "Screw it!" With all the time we lost, we just accepted the fact and tried to enjoy the rest of the day. (Which we did) Because of this, we did more travelling to other groups to see their projects than work on our own, and ended up submitting Whack-a-Ship, as the original game couldn't be salvaged, and Pong was uncomplete due to syncing errors. (But [here's](https://github.com/ROODAY/Jong) its spiritual successor, with 4 players)

{% http://i.imgur.com/4dpKk6A.png 640 360 Jong %}

&nbsp;&nbsp;&nbsp;&nbsp;We didn't win anything of course, due to the huge mistakes that were made, and not to mention the insanely good projects that were submitted, the first place one being an etch-a-sketch built off an arduino that saved the sketches to a .stl file that could be 3D printed. (Mind = Blown) But despite that, we did learn a lesson from LexHack: **Don't Get Too Ambitious!** The biggest problem with RTShips was that we expected to do so much more than was actually possible in 12 hours. It was our first hackathon, none of us really knew how to use Phaser.js or Socket.io very well, and we were two men short. Had we chosen a simpler project and commited to it, even something as simple as Pong, we might've placed! Ambition is a good thing to have, but overestimating your skill will most likely end with a pretty bad result. It may not be as bad as Whack-a-Ship, but still, pretty bad.

{% http://i.imgur.com/IX6Zapx.png 640 360 The Almighty Whack A Ship %}