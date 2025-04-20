+++
title = "Figuring out Layton vs Ace Attorney's extra content"

[taxonomies]
tags=["3ds", "layton", "ace attorney"]
+++

Or the tale of how the 3DS' filesystem is a complex pile of a million different layers of encryption and hashes.

Fun!

<!--If you just want a guide, check [here](link-here).-->

<!-- more -->

---

Professor Layton is probably my favorite videogame series of all time, as anyone who's talked to me for longer than five minutes can probably confirm. So it shouldn't surprise anyone that I'm currently in my second full 100% replay of the series, and this time trying to be as thorough as possible. I'm talking not just all puzzles, but also hint coins, collection, and of course, the bonus content.

In case you weren't aware, the Professor Layton series - the mainline games at least, and yes, this includes vs - all include some sort of content unlockable over time after the game releases. Usually this comes in weekly or daily puzzles, but the crossover with the Ace Attorney series went in a slightly different way - having concept art and some slightly unfunny, fourth-wall breaking epilogues (which themselves include puzzles) release during the months immediately after the game's release, for example, April to September 2014 in Europe, where I live. This content is usually referred to as DLC by fans of the series, and I might refer to it as such every now and then - but strictly speaking, this isn't actual DLC.

How's that? Well, for all eight games with bonus "downloadable" content, there's no actual *content* being *downloaded* to your console. All that happens is that you connect to the online servers, and they unlock existing content if the game servers report that a certain day has passed. So all the content for the entire 6-12 months already existed in the cartridge even on launch day. The only exception to this general rule is Layton's Mystery Journey, LEVEL5's 2017 attempt to revive the series, which for some reason included both paid DLC and "daily puzzle" type content. Specifically the original 3DS/mobile version, the Deluxe version for Switch made all the DLC free. The biggest mystery in this journey is how they fumbled this game so much in every possible aspect (and I'm saying this as someone who really appreciates what it was trying to do).

Now, I'm no baby Layton fan; I've been here since the very beginning and I own all the games available in my region, physically. So when I was playing either the first four DS games, the incredibly good (fight me) non-crossover 3DS titles, or the aforementioned Mystery Journey, the fact that my original 3DS had broken a couple years ago and I was playing on a different console was absolutely no problem, since this "unlock state" got stored in the cartridges as part of the save file. However, probably thanks to CAPCOM's involvement in this game, that's not actually the case specifically in Layton vs Ace Attorney! Instead, the game stores it as "extra data", which is stored in the SD card. And my old 3DS is lying in a drawer as two separate screens.

Well, I guess it's time to really learn what extra data is!

# What is extra data?

The 3DS was the last Nintendo console to store game data on the cartridge itself for physical games - the Switch decided to go with a profile-based system like the Wii U, which would've seriously complicated storing save files in one cartridge. (Also, cartridges' save files was a common way to hack the 3DS for a couple years, with the Action Replay Powersaves letting you just insert your own save files on it, so obviously Nintendo wanted to avoid security flaws like that).

However, it doesn't store *everything* in the cartridge. For example, update data or DLC is too hefty for the read/write memory in the 3DS cart itself (for some games this can be half the size of the actual game, or even more), so it gets stored inside the console's SD card instead. Separately, StreetPass and SpotPass data is tied to your console, so it makes sense to keep it contained in the SD card (which can't be used in another console), so it gets thrown in "extra data", which is basically a subset of save data that always gets stored in the SD card. Everything else that is stored in extra data is up to the developer of the game - but usually, it's very little content, less than 1 block (128KB). Obviously, if you're playing a digital copy of a game, everything is in the SD card anyway.

(Some games, most notably Super Mario Maker, either link the save to extra data or just straight up store the save as extra data, which means that the save is always in the SD card for those games, but that's not really relevant to our situation today.)

Here's a graph that summarizes this explanation:

![Graph that explains the relationship between game data, extra data, and the 3DS memory](/images/2025-04-20-01-extra-data.png)

# Wait, wait. StreetPass? SpotPass? What are those?

If you don't know what StreetPass and SpotPass are, chances are, you either never owned a 3DS or didn't really pay attention to the built-in software. I'll brush over StreetPass really quick, because the one that's relevant to today's topic is SpotPass.

StreetPass was a feature in the 3DS where you could share data from your games with people you passed on the street while your 3DS was on but in standby. It didn't really get a lot of usage, and its main thing nowadays is making Nintendo fans feel like multiplayer was intentionally made worse in 3DS games (even though I do love StreetPass and I wish it would return in some way).

SpotPass, though, was a completely different feature where your console would recieve information about games you played at anytime the console was on and connected to the internet, even if you weren't actively playing the game or the game wasn't even inserted. This is also how the system showed you notifications for events ingame, and the Switch did use a modified version of this system for things like the news or Splatoon's events.

Now, Layton vs Ace Attorney stores both SpotPass data and a separate "unlock key" in your console, so I was curious if there was any way to play the extra content nowadays that the servers are completely shut down.

# The part where I try multiple different things and they all fail

The most obvious - and least likely - solution was to just see if specifically the server for this game had been left up. I don't know what I was expecting but it obviously didn't work. This, though, is where I found out what extra data was, because the game generates empty extra data even if it's unable to fetch anything. So I asked around to see if anyone could dump the extra data from their own game, and to see if it would work on mine.

It didn't.

At the time, I was missing the SpotPass data, which is stored in a separate directory and is kind of annoying to deal with, so I wasn't even sure if it was a thing. So I decided that it probably was some sort of region / version locking thing (this game has two separate european versions, and we had different ones), so I just gave up and left it there for months. Woo!

Recently, though, I asked again, and I looked around a bit harder at my hard drive, to see if I had any kind of backup of my old SD card from my 3DS that broke (again - split in half), and I found it! There, in a random folder sitting somewhere stupid, named `Old 3DS backup`, was a complete SD card archive. Woo! (for real this time)

Unfortunately, Nintendo doesn't exactly store your 3DS' files in plaintext, for extremely obvious reasons. So decryption time it was. I'm sure I won't lose my mind over this, right?

## The part where I lose my mind over encryption

Okay, so let me be fully honest. This isn't my first time dealing with 3DS encryption. I've had my current 2DS' SD cards die, had to dig around for savefiles in a half-corrupted mess of an SD card, etc. etc. etc. The difference this time, though, was that I did not have the decryption key for my old console. I have no clue why I didn't archive this - especially because it's required to mod the damn thing, and I 100% modded it like seven years ago or something - but it meant that I had to manually bruteforce the lil' fucker.

Fortunately, there's a well-known process to do this from either Friend Code Local Storage (so adding someone as a friend), or a QR code of a Mii. Unfortunately, it's still bruteforcing a decryption key and that's basically just cryptomining lite. Un-unfortunately (refortunately?), I had just gotten myself a chonky new GPU I could use for this.

Ten minutes of dealing with drivers and unmet dependencies later (I'll skip the explanation to avoid giving people too many headaches in a row), I had Seedminer running with an old QR code of a Mii I made on my old console! (If you want an explanation on how Seedminer works, check [this presentation](https://zoogie.github.io/web/34%E2%85%95c3/) by zoogie!). This did make my PC unusable for fifteen minutes, but in the end, I had a shiny new decryption key! Last time this took several hours lmao.

## The part where I realize SD encryption isn't the only measure the 3DS has

So, I had some decrypted "raw" extra data files, which according to [3dbrew](https://3dbrew.org), a really good resource for 3DS technical knowledge, were DIFF containers. I decided to go the lazy route and just plop them, reencrypted, into my 2DS' SD card and see what happened.

Obviously, because I hadn't suffered enough, they didn't work at all. In fact, my brand new extra data was totally messed up, and it showed as a (?) icon in my settings app. So, seeing that, I thought "well, maybe there's some console-specific data here", and I re-checked the page for DIFF (the container format that the 3DS uses for extra data) to see what it could be.

And lo and behold, there's a signed hash in the beginning of the file. Welp.

In case you don't understand a single word from that sentence, a very simple summary is that the file includes a check that both requires the file to not have changed a single bit (to check if it has been modified without authorization), and also requires a specific encryption key to be used when making the file, which is stored only in the console itself.[^1]

And the encryption key here is a different, console-specific key.

Fuck me.

So, since I wanted to make this accessible to as many people as possible, I decided to try and look for ways to install this extra data into the console, without needing to extract your encryption keys into your PC, and then modify the file or whatever. Obviously, Checkpoint does this for regular extra data, but around this time, I had realized that pesky SpotPass data was also there, and it probably had something to do with this whole mess. So I took to Google and I looked for ways to make this thing work somehow.

# oh god why didnt i look this up before

Unfortunately, I stumbled onto the classical modder's issue: somebody had done a lot of the work that I had been doing a whiiiiile before I was able to. Oopsies.

[This site](https://plvspwaa-dlc-guide.pydraxalpta.com), by pydraxalpta (also known as Pyras), at the time of finding it, described the process of importing the extra data and SpotPass data into the Citra/Lime3DS emulator. This did confirm that SpotPass data was required to function - what I assume is going on is that the game is not only trying to recieve the "unlock key", but it's also double-checking it against SpotPass data, which should be broadcast to all 3DS's connected to the Internet. Which makes sense, but makes things a tad more complicated for me.

That said, I looked into it a little bit further and I realized there was a link pointing to a vague GBAtemp post explaining how you could copy SpotPass data through FBI (a title manager for the 3DS that also works as a general purpose file manager if you're insane enough) (I'm only half kidding, its controls and options aren't exactly the best).

So what I did was, I tried to follow the instructions as well as I could to import my old SpotPass data into my current 2DS' SD card. I needed to create the extra data from within the game first - you can't just create extra data for games for several reasons, one of them being that you need to rip the icon from the game and that would be really annoying to do in a homebrew app - but then, I imported both the regular extra data and the SpotPass data. I opened my game, and... well, it worked!

Finally, I could play not-exactly-top-tier bonus content from a crossover that is massively underrated by whatever semblance of a community Professor Layton has. Woo!

But, my struggles weren't exactly over yet, because when I contacted Pyras, to ask them to update their site with newer instructions, I tried to get some screenshots on the other European version of PLvsAA, so I could get them in English rather than Spanish (no, luma locale switcher wasn't an option, that shit is broken. and also i didn't want to have to manually type in the locale file. yes it was more worth it to try this with a different, 1.5GB copy of the game I already own. shush.)

# And when I thought it was over...

So, it didn't work. Obviously. Otherwise I'd already be writing a conclusion.

I gathered from comparing my files with Pyras' that this was definitely some sort of version-locking issue with the SpotPass data. The files for the regular extra data were identical to the bit, but some of the first 32 bytes in the SpotPass data were different. Thankfully, at this point I had been staring at this game's internals for so long that I recognized the title ID somewhere in that file's header. Something else that was also there was a seemingly random list of bytes, which I think are either some sort of console identifier or the 3DS' MAC address[^2] or something. I decided to just scrub that, too, even though the 3DS servers are already dead so Nintendo can't exactly ban me if there's nothing to ban me from.

And hey, it worked! Changing the title ID to whichever version I was trying to run didn't cause me any issues, and scrubbing whatever that ID was didn't cause any issues either. So, I needed to distribute four copies of basically the same file, but the data is like 1600 bytes in total already so it's not really an issue.

So, this is where we're at right now. I've asked Pyras to update their guide with this new information. There's a chance that when you read this, it's already updated, so check it out! I really appreciate them documenting this, because otherwise I wouldn't have found myself in that GBAtemp post that told me that what I wanted to do wasn't some sort of pipe dream I had to do by myself or something.

The only possible issue I can think of at this point is the Japanese version being coded completely different somehow, which wouldn't surprise me considering there was a two-year gap between the release of this game in Japan and overseas. [Wouldn't be the first time I encountered this, either](https://rhwiki.net/wiki/Rhythm_Heaven_Megamix). (If you want more details on that, I'll try to get some Rhythm Heaven modding blog posts out somewhat soon. Hopefully earlier than the time it took me to make this one post.)

# Conclusion

The 3DS is a cursed device and every single hour I spend learning how it works I wish I knew less. Please help

---
# Footnotes

[^1]: Computerphile has a great explanation on how hashing works if you're interested (and it features Tom Scott!): https://www.youtube.com/watch?v=b4b8ktEV4Bg
[^2]: TLDR: the MAC address is a unique identifier for an Internet device, like the 3DS' wifi card