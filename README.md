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
Milestone 3 Devlog goes here.
## Final Devlog
Final Devlog goes here.
## Open-source assets
- Cite any external assets used here!
