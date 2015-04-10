---
layout: post
title: Patch - Tournaments
date: 2012-01-05 15:16:17
comments: true
categories: old days, starcraft, php
id: 3783813953
original: http://starcraft.rickyayoub.com/news.php?id=51
---

Based on everybody's feedback from the last tournament that we ran, I've made the following adjustments:

Things you as the user will notice:

1. The page can be safely refreshed after reporting a victory, you won't be advanced two rounds now.
2. The second place "Report Victory" button will not stay after the tournament ends
3. I added a refresh link in the upper right of tournaments just to reduce future refresh issues

Behind the scene things that you won't notice:

1. The page can be refreshed after checking in, users won't be re-assigned tournament IDs
2. Setting a tournament to check-in mode does not lock the brackets
3. Tournaments will now be seeded by points when they are started
4. New tournaments will not be created in running mode
5. Setup Tourney button looks nicer
 

That's all folks! 