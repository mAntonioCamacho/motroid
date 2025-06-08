[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/6nx_gS-F)
# GDIM33 Demo Project

## Milestone 1 Devlog
Player Graph asset: https://github.com/UCI-GDIM33/vertical-slice-BulkyCaulk/blob/main/Motroid/Assets/VisualGraphs/Player%20Graphs/player-graph.asset
Player Input Actions: https://github.com/UCI-GDIM33/vertical-slice-BulkyCaulk/blob/main/Motroid/Assets/Input/Player/Motroid-Player-Move.inputactions
I believe I didn't overscope. Originally I wanted to implement a boss, but from the performance of my game in browser leaves me wondering if it is even worth continuing this project. I may have to restart and scope way down, so that the game can run smoothly. I still think what I had is doable, but if I can't fix the performance, then this project is dead. I don't think the systems I had wanted to build were that complex since I would have given them one or two mechanics, such as boss spin around until it sees player, then go that direction. 


## Milestone 2 Devlog
Nav Meshes:           https://github.com/UCI-GDIM33/vertical-slice-BulkyCaulk/blob/main/Motroid/Assets/Scenes/Level/NavMesh-Corridors.asset
                      https://github.com/UCI-GDIM33/vertical-slice-BulkyCaulk/blob/main/Motroid/Assets/Scenes/Level/NavMesh-Floor.asset
            
Enemy State Graph:    https://github.com/UCI-GDIM33/vertical-slice-BulkyCaulk/blob/main/Motroid/Assets/VisualGraphs/Enemy%20Graphs/Enemy.asset

Enemy Animator:       https://github.com/UCI-GDIM33/vertical-slice-BulkyCaulk/blob/main/Motroid/Assets/Art/Enemy/Animations/Enemy.controller

The enemy transition from idle to walking in the enemy state machine and the animations were a difficult process. I was having trouble with the animation since I was unsure of the generic type, where in class we talked about the humanoid type. My enemy is a generic type so I had to figure out the differences and learn how to set it up. I did end up getting it to work, but I'm not sure if the steps were any different. I took a break from it and then came back to see it working. I'm fairly certain I did get it to work before my break, but I must have not noticed its animation since its idle state doesn't move that much. The brunt of the work lies inside the transition from idle to walking. I wanted the enemy to "scan" the area so I had a vector changing directions from one vector to another, creating a 2d cone shape. Within that shape I would ray cast from the changing vector and trigger an event that would set variables for the transition to happen and to switch the animation. The issue was the math. One example I can remember was the changing vector being set to the value of the static vector so that it could reset its position and start the scanning effect, but being somehow greater than the static vector. I assumed it had to do with float values not being precise so I added an offset. 


## Milestone 3 Devlog
Shader Graph:         https://github.com/UCI-GDIM33/vertical-slice-BulkyCaulk/blob/main/Motroid/Assets/Shader%20Graph/Sun.shadergraph

Does shrinking my scope count as progress? I had to scrap and remake the level I had to account for the changes I made some player mechanics. Originally a dash was implemented, but the gameplay wasn't fun, so I scrapped it and turned it into a jetpack. The original level was designed around the dash mechanic, so that needed to redone. Now the goal of the gameplay is to have the player 
 - access a generator to turn on the power, the power will open a door to the powerup
 - make their way back to the power up, fighting through waves of enemies 
 - get the power up
 - use the power up to traverse towards the upper layer of the level
 - maybe fight an invincible boss that the player will need to eject from the room or just eject something from the room or escape sequence

The shadergraph doesn't really play any role, its supposed to be a sun/star, but I couldn't find a good texture to animate. I decided to just have the player hair texture on it. The animation does play a bit fast, but that's probably because I am multiplying the texture by time. I'm certain I could slow it down by making time slower, but like I said, it really doesn't play any role. I wanted the game to be a bit darker, and the only light source to be the sun. However, for some reason, the light seems to light everything even when objects should block it out. The shadows aren't shadowing in simpler terms. Even with no light in the scene, the materials on the structures give off a faint yellow glow. At this point it's either I multiply the texture for every different texture in the scene or finish the gameplay.  


## Final Devlog
The player can look around, shoot, and jetpack. This iteration has the player looking for the jetpack/fire extinguisher. Player leaves the spawn room and should see the extinguisher behind a locked gate. Player should then see two ways to go, one blocked by not being able to jump high enough and an other way leading downstairs. Going downstairs leads to storage room. Traversing the room enough should lead the player to a bright red button. Upon pressing button, the power "turns off", - may not always work in itch - music changes and enemies spawn repeatedly upon their death. Player must make their way back to locked gate since power is off, and then grab the item. After getting jetpack, player can now go to blocked off area by using jetpack to get to 2nd level. Traversing forward leads to a new item, a flare, and then leads to the boss room. Boss will see player only if player is on the ground. Boss can't be killed by gun and player must traverse the room to look for 3 buttons. Upon pressing a button, a beacon appears. The player must lead the boss to the beacon to trigger an event that damages the boss. This will be done 3 times. After boss is dead, escape sequence starts and player must make their way towards the exit and reach the portal before the timer runs out. Upon player's death, a new scene will load where they are allowed to choose between replaying or quitting. Escape portal changes scene to win area, similar to death scene area.

The gameplay activated visuals - hopefully - help the player to defeat the boss. They are activated by pressing the buttons in the boss room. Pressing one will show a beacon. When player leads boss to beacon, the boss will stop, a bright light will shine upon the boss, lightning effects zap the boss, and then it stops and explodes, with a fire lingering. 3 times. 
All of these effects are events within script graphs(script machines and state machines). The enemy spawner uses a state machine. It has two states, on and off. The spawner turns off when there are 24 enemies within the scene. When a player shoots an enemy, the enemy counter is reduced, the enemy is destroyed, and then the spawner is turned back on. 
Another script machine is on the buttons in the boss room. This script machines controls the events of how and when the particles systems execute. The button waits for player input, and then executes the steps above when I mentioned the gameplay activated visuals. 


## Open-source assets
## Assets used
[Sci-fi PSX Style Heavy Machine Gun - V1](https://millennial-voxel-forge.itch.io/sci-fi-low-poly-v1)
[Kim Lightyear - Destiny (Wave G)](https://opengameart.org/content/destiny-wave-g)
[Sci-fi Guns SFX Pack - Mikael Vanninen](https://assetstore.unity.com/packages/audio/sound-fx/sci-fi-guns-sfx-pack-181144)
[Sci-fi Construction Kit (Modular) - Sickhead Games](https://assetstore.unity.com/packages/3d/environments/sci-fi/sci-fi-construction-kit-modular-159280)
[PSX Sewerfiend Animated - ROKAY3D](https://www.fab.com/listings/5fd24ce7-f7ef-4866-82cd-0a161ca5acd5)
[Franky - 06hypersonic60](https://www.models-resource.com/playstation_3/onepiecepiratewarriors/model/5432/)
[Free Quick Effects Vol.1 - Gabriel Aguiar Prod](https://assetstore.unity.com/packages/vfx/particles/free-quick-effects-vol-1-304424)
[Grenade Sound FX - MGWSoundDesign](https://assetstore.unity.com/packages/audio/sound-fx/grenade-sound-fx-147490)
[Alarm Sound Effect - bonzille](https://opengameart.org/content/alarm-sound-effect)
[Synth/Metal Climax Theme - Gradoa](https://opengameart.org/content/synthmetal-climax-theme)
