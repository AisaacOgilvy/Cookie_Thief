<p align="center"><img src="images/title.png" width="800"></p>

# The Great Mars Cookie Heist
### Girl Scout vs Boy Scout

A Python video game you play inside a Jupyter notebook. Pick your badges, battle the evil Boy Scout on Mars, and win back the cookies. It has its own funny songs, made with AI, that play at every big moment.

Made by Isaac Boruchowicz for Hex NY *Intro to Creative Coding*.

---

## The story

<img src="images/rovey_hello.png" width="220" align="right">

*Once upon a time, on the red sands of Mars,<br>
a Girl Scout was sleeping in her tent under the stars.<br>
Her cookies were tucked in, all cozy and sweet...<br>
until an evil Boy Scout crept in on his sneaky feet.<br>
By morning the jar was empty, just crumbs on the floor.<br>
Now it's up to you to settle the score.*

<p align="center"><img src="images/boy_steals_cookies.png" width="420"></p>

---

## How to play

**What you need:** Python 3. Then type this in Terminal, inside the game folder:

```bash
pip install -r requirements.txt
jupyter notebook "Girl Scout Vs Boy Scout.ipynb"
```

Press **Enter** after each line. When Jupyter opens the game, click **Run → Run All Cells**.

### How a game goes

1. **Type your name.**
2. **Talk to Rovey** about the cookie jar.
3. **Pick an outfit.**
4. **Pick your badges:** 2 attacks, 1 health badge and 2 special badges.
5. **See your loadout** next to the Boy Scout's.
6. **Battle!** Every round you pick 1 attack, plus 1 extra if you want. You attack first, then the Boy Scout fights back.
7. **First one to 0 health loses.** If you both hit 0 in the same round, a coin flip decides.

<p align="center">
<img src="images/girl_outfit_a.png" width="150">
<img src="images/girl_outfit_b.png" width="150">
<img src="images/girl_outfit_c.png" width="150">
&nbsp;&nbsp;&nbsp;
<img src="images/boy_scout.png" width="150">
</p>

---

## The badges

You have **100 health**. Attacks can be used every round. Health and special badges work **once per game**. The Boy Scout gets his badges at random, and you can always see what he has left.

### Attacks (pick 2)

| | Badge | Power | What it does |
|---|---|---|---|
| <img src="images/badge_fire_safety.png" width="60"> | Fire Safety | Fireball | Either fizzles (1–3) or blazes (22–25), nothing in between |
| <img src="images/badge_electricity.png" width="60"> | Electricity | Lightning Hands | 8–14 damage |
| <img src="images/badge_astronomy.png" width="60"> | Astronomy | Meteor Strike | 5–18 damage |
| <img src="images/badge_chemistry.png" width="60"> | Chemistry | Potion Bombs | Always exactly 10 |
| <img src="images/badge_archery.png" width="60"> | Archery | Rain of Arrows | 0–36: could miss, could hit huge |

### Health (pick 1)

| | Badge | Power | What it does |
|---|---|---|---|
| <img src="images/badge_first_aid.png" width="60"> | First Aid | Healing Aura | Heals 0–50 |
| <img src="images/badge_lifesaving.png" width="60"> | Lifesaving | Revive | If you get knocked out this round, you come back with 18. If not, +5 |
| <img src="images/badge_camping.png" width="60"> | Camping | Base Camp | Hide in your tent: their attack turns into health for you |

### Special (pick 2)

| | Badge | Power | What it does |
|---|---|---|---|
| <img src="images/badge_dog_care.png" width="60"> | Dog Care | Guard Dog | A cute dog distracts them, so their attack does nothing |
| <img src="images/badge_rover_repair.png" width="60"> | Rover Repair | Rovey Boost | Rovey doubles your attack |
| <img src="images/badge_salsa_dance.png" width="60"> | Salsa Dance | Copycat Groove | Their attack bounces back and hits them |
| <img src="images/badge_magician.png" width="60"> | Magician | Double Trouble | Gives one of your other badges an extra use |

All the numbers live in [`data/badges.csv`](data/badges.csv). Change a number there, and the game changes with it.

---

## Rage Mode

<p align="center">
<img src="images/boy_rage_potion.png" width="300">
<img src="images/boy_rage.png" width="300">
</p>

**Why I added it:** I wanted to make sure the Girl Scout would never have it too easy, or too big of an advantage, once you discover the right loadout and strategy.

**How it works:** when you're crushing him, the Boy Scout cheats and drinks a **rage potion**. From then on, **his attacks hit 2x as hard for the rest of the game.**

Rage Mode is checked right after your attack, before he hits back. It turns on if **any one** of these is true:

| Trigger | Rule |
|---|---|
| 1 | Boy Scout has under **18** health and you have over **36** |
| 2 | Boy Scout has under **9** health and you have over **18** |
| 3 | You have **72% more** health than the Boy Scout |
| 4 | You are winning by **more than 36** health, from a big attack or from healing |

---

## The music

All the songs were made ahead of time with **Google Lyria 3**, an AI music model:

1. **Made:** each song has its own cell in `curl_test.ipynb`. Running a cell asks Lyria for that song.
2. **Saved:** the same cell saves the song as an MP3 in the `music/` folder.
3. **Pulled:** when the game starts, it loads every song from `music/` and plays each one at its moment.

So you **don't need a Google key to play**, only to make new songs. If a song file is missing, the game just skips it.

| Song | Prompt |
|---|---|
| **`intro.mp3`**<br>start menu | fun remix of the classic kids clapping chant Who Stole the Cookie from the Cookie Jar with a bouncy spacey Mars hip hop beat synths and hand claps kid friendly and catchy. Lyrics: Who stole the cookie from the cookie jar? Who stole the cookie from the cookie jar? Was it you? Could not be! Was it me? Not me! Then who? Who stole the cookie from the cookie jar on Mars? Somebody sneaky under the stars! |
| **`thief.mp3`**<br>cookie thief game over | funny dramatic cartoon soap opera song with a shocked gasp sad violins and a goofy trombone kid friendly. Lyrics: Oh no how could it be? The cookie thief was you not me! Crumbs on your fingers and chocolate on your face! Rovey is crying all over the place! Game over game over what a disgrace! |
| **`stolen.mp3`**<br>cookie stolen | dramatic funny cartoon villain reveal song with a big gasp sneaky tuba and spooky organ kid friendly. Lyrics: Oh no it was the Boy Scout all along! He grabbed the cookies and he ran off with a song! Sneaky little Boy Scout you are such a thief! Girl Scouts are coming to give you some grief! |
| **`picking.mp3`**<br>picking badges | sneaky suspenseful but goofy cartoon tune with a ticking clock beat and plucky strings funny and kid friendly. Lyrics: Tick tock Girl Scout it is time to choose! Pick your badges so you do not lose! The Boy Scout is sneaky the Boy Scout is sly he stole all your cookies and he will not say why! |
| **`loadout.mp3`**<br>loadout | funny upbeat bouncy cartoon hype pop song that gets you pumped. Lyrics: Check out your loadout shiny and new! The Boy Scout is shaking he does not know what to do! Badges on your sash ready for the fight the cookies are calling so hold on tight! Check out your loadout it was made for you now make that sneaky Boy Scout go SHOO! |
| **`battle1.mp3`**<br>battle | fast 8-bit chiptune video game boss battle music retro arcade fighting game stage 160 bpm intense and catchy funny. Chant lyrics: Girl Scout Girl Scout fight fight fight! Boy Scout Boy Scout that is not right! Give me back my cookies give them back tonight! |
| **`battle2.mp3`**<br>battle | rock video game battle music like a fighting game stage shredding electric guitar riff and pounding drums high energy funny. Crowd chant lyrics: Hey Boy Scout we know it was you! Cookie crumbs are on your shoe! Girl Scouts rock Boy Scouts flop we will not stop till the cookies drop! |
| **`battle3.mp3`**<br>battle | epic orchestral video game boss battle music with a heroic choir like a final boss fight in a fantasy adventure game dramatic but funny. Choir lyrics: On the red sands of Mars the battle is told the Girl Scout fights for the cookie of gold! The Boy Scout trembles his knees start to shake he knows those stolen cookies were a big mistake! |
| **`battle4.mp3`**<br>battle | fast intense 8-bit chiptune video game boss battle music retro arcade fighting game stage instrumental only no vocals no lyrics |
| **`battle5.mp3`**<br>battle | epic video game final boss battle music with orchestra pounding drums and electric guitar intense and exciting instrumental only no vocals no lyrics |
| **`rage.mp3`**<br>rage mode | dramatic intense cartoon villain song heavy drums distorted electric guitar and an evil laugh scary but silly and kid friendly. Lyrics: Uh oh uh oh he drank the potion! Boy Scout rage mode set in motion! Double the power red in the face hold on tight Girl Scout it is a cookie chase! |
| **`winner.mp3`**<br>winner | funny happy cartoon victory song with a cheering crowd and brass horns. Lyrics: The Girl Scout wins the cookies are back! The Boy Scout is crying he lost his snack! Hip hip hooray it is a cookie parade the best Girl Scout that Mars ever made! |
| **`loser.mp3`**<br>loser | funny silly sad cartoon song with a goofy sad trombone slow and dramatic kid friendly. Lyrics: Oh no oh no the Boy Scout won he is eating your cookies and having fun! Crumbs on his face and a smug little grin maybe next time you will finally win! |
| **`salsa.mp3`**<br>salsa dance | fun upbeat latin salsa dance song with trumpets congas and maracas playful and funny. Lyrics: Salsa salsa spin around! His attack bounces back down! Shake those hips and move those feet the Boy Scout falls down he cannot take the heat! |

Every round, one of the 5 battle songs is picked at random.

### Easter egg: the salsa song

<img src="images/boy_fire_safety_salsa.png" width="160" align="right">

If **you** (not the Boy Scout) use **Salsa Dance**, the game plays a secret salsa song:

> *"Salsa salsa spin around! His attack bounces back down! Shake those hips and move those feet!"*

<br clear="right">

---

## What's in the folder

| | |
|---|---|
| `Girl Scout Vs Boy Scout.ipynb` | The game |
| `data/badges.csv` | Every badge and every number in the game |
| `images/` | All the game art |
| `music/` | All the pre-made songs (MP3) |
| `curl_test.ipynb` | Where the songs were made with Google Lyria 3 |
| `requirements.txt` | Python packages to install |
