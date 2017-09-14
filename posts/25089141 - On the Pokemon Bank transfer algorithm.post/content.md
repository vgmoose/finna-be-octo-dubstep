---
layout: post
title: On the Pokémon Bank transfer algorithm
date: 2017-09-13 20:21:57
comments: true
categories: pokemon, pokemon bank, youtube
id: 6446734174
hidden: true
---

I uploaded two videos to YouTube a few months ago describing the transfer algorithm in the 1.2 version of Pokémon Bank for the 3DS. The process was upsetting as it was not a consistent, deterministic algorithm, and instead generates completely random numbers at the time of transfer to create the Gen 7 Pokémon from Gen 1 ones.

- [First video](https://www.youtube.com/watch?v=9ov9HrWOlH0) explaining the algorithm and what values it discards/randomizes
- [Second video](https://www.youtube.com/watch?v=NwBbA8_KYSQ) showing the transfer process on some cloned Pikachu.

What I describe in the videos is not how transfers in previous generations have ever worked.

In the videos I demonstrate that if you transfer 10 of the same exact Pokémon going in, they come out as 10 totally different Pokémon. They have been randomized. In every single previous generation, the algorithm to convert between generations is deterministic.

This is the first time randomness is applied such that even exact clones going in come out randomized.

- **Gen 1 <-> Gen 2** These games used the same data structure. Hold item, gender, and shininess are preserved across transfer.
- **Gen 3 -> Gen 4** Transferred via Pal Park, all data is preserved and consistent. Clones of the same Gen 3 Pokémon will always result in the same Gen 4 Pokémon. [More info]( https://bulbapedia.bulbagarden.net/wiki/Pal_Park#Modifications_to_transported_Pok.C3.A9mon).
- **Gen 4 -> Gen 5** Transfered via Poké Transfer, all data is preserved and consistent. Clones of the same Gen 4 Pokémon will always result in the same Gen 5 Pokémon. [More info]( https://bulbapedia.bulbagarden.net/wiki/Poké_Transfer#Modifications_to_transported_Pok.C3.A9mon).
- **Gen 5 -> Gen 6** Transfered via Pokémon Bank, all data is preserved and consistent. Clones of the same Gen 5 Pokémon will always result in the same Gen 6 Pokémon. Some Pokémon may become shiny since Gen 6 loosened the Shiny odds, but it would be consistent across clones. [More info]( https://bulbapedia.bulbagarden.net/wiki/Poké_Transporter#From_Generation_V).
- **Gen 6 -> Gen 7** Transfered via Pokémon Bank, all data is preserved and consistent. Clones of the same Gen 6 Pokémon will always result in the same Gen 7 Pokémon.

And then we come down to the topic of the videos, **Gen 1 -> Gen 7** transfers. At the time of the video, IVs and gender were completely randomized. Meaning, ten identical Pikachu in Gen 1 (seen in the [second video](https://www.youtube.com/watch?v=9ov9HrWOlH0)) transferred to Gen 7 become ten different Pikachu in Gen 7. You can see that despite them being clones, after transfer they are all different.

The IVs and EVs that originally made up the original Pokémon are discarded completely, except for the shiny check. Nature is determined via EXP, a constantly fluctuating feature of a Pokémon. Transferring one clone, winning a battle, then transferring another clone, would result in two different natures in Gen 7. [More info](https://bulbapedia.bulbagarden.net/wiki/Poké_Transporter#From_Generation_I).

*None* of the previous generation transfers have ever used randomness to determine any new values. Not only that, but they've never used something temporary like EXP to determine new values either.

As of the uploading of the video, if this same algorithm were used on the GSC virtual console games, Pokémon would be randomly changing gender, and wouldn't maintain shininess after their transfer. This was such an issue that now an update to Pokémon Bank has been released that no longer randomly chooses a Gender, and correctly calculates shininess. It still randomizes the IVs and chooses the nature based on EXP.

My whole point is just that it feels careless and lazy. Ever since Gen 3 broke backwards compatibility, fans and the community have written several (deterministic, not random) algorithms to convert from Gen1/Gen2 format to newer formats. Pokémon Bank's official "solution" throws all that out the window, and randomizes it!

And now with the new 1.3 update to Pokémon Bank, depending on whether you transfer before or after the update, you will get varying degrees of randomness between the two versions. I still don't think they have a good transfer algorithm in 1.3, and they won't until they remove all the randomness. However, it is nice to see that they are now consistent for some aspects of Gen 2 (gender and shininess).

The [first video](https://www.youtube.com/watch?v=9ov9HrWOlH0) goes into more detail on what's actually happening to the data, and what parts specifically are randomized.

Some other comments on either video don't see the value in keeping the transfer algorithm consistent between clones. If that's the case, we may as well just randomize stats every time we deposit a Pokémon in the PC. Where's the line: if we're going to start disrespecting the backbone of the Pokémon's data, why do any of the "individuality" aspects of the Pokémon franchise matter?

I strongly believe that the Pokémon Company should stick to keeping the "DNA" of the Pokémon consistent, as they have in the past. To randomize it is just a cop-out. [Here](https://www.youtube.com/watch?v=NwBbA8_KYSQ&lc=z13xzzcqds2merev223ddxkwrtfwc55b204.1487816879691123)'s a good comment that summarizes this point of view. This consistency an important attribute to minimize the arbitrary-ness of it all.

And as one final closing thought, and something I probably didn't drive home enough in the videos, is it would've been *VERY* easy to keep this consistent between clones! For one, they could have simply seeded the Random Number Generator with the Gen 1 Pokémon's IVs. It would still be basically random, but consistent across the same Pokémon being transferred. Another way to do it is doubling the IVs to fit into the new IV structure, and converting the EVs as well as possible into the new EV format.