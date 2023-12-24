# Game Design Doc

## Game Overview

This game follows a gameplay style similar to Frogger, where the player controls a cat navigating through a grid-based city. The cat can hop in four directions to cross roads while collecting points for each successful road crossing and each slize of pizza collected. The primary objectives include crossing roads before the camera progresses out of view and avoiding increasingly faster traffic as the game advances. If the player fails to avoid these, they die and reset, with the ultimate goal being to get the best highscore.

### Mobile Suitability

The game design is well-suited for mobile devices as shown below:

- **Session Lengths:** The game offers relatively short session lengths, enabling players flexibly with regards to starting and stopping gameplay conveniently.
- **Interruptions:** Seamless saving and loading mechanisms reduce the impact of interruptions on gameplay, ensuring a smoother gaming experience.
- **Touch Screen Integration:** Gesture-based controls enhance gameplay, ensuring easy and intuitive navigation through the game's mechanics.

## Gameplay
- **Hop Mechanics:** Players control a cat character that can hop in four directions—forward, backward, left, or right—on a grid-based system. Precise timing and strategic movements are required to navigate across various obstacles.
- **Traffic Challenges:** Roads are filled with moving vehicles, presenting obstacles that players must carefully maneuver through. The traffic speed increases gradually, adding complexity and challenge to the gameplay.
- **Environmental Obstacles:** Apart from traffic, there are static environmental obstacles like roadblocks and other barriers that obstruct the cat's path, requiring careful planning to avoid or navigate around.
- **Dynamic Camera Movement:** The camera continually moves forward, compelling players to keep pace and advance through the game. This feature limits lateral movements, heightening the challenge.
- **Collectable Pizza Slices:** Pizza slices act as collectibles, rewarding players with 10 points for each slice collected. This incentivizes players to deviate from the direct path, balancing risk and reward.
- **Continuous Progression:** Similar to Crossy Road, the game lacks a definitive endpoint. Instead, players strive to achieve higher scores by surviving longer, crossing more roads, and collecting pizzas to increase their scores.


## Game Progression
- **Character Progression:** The game follows a continuous progression model, similar to Crossy Road. There isn't a specific ending, instead, players aim to achieve higher scores and overcome their previous records. This is reflected in the highscore system which can be saved/loaded from the menu.
- **Winning/Losing Conditions:** There is no win/lose scenario. Players continue playing until they fail to navigate through the obstacles or make an error, ending their current run. The primary goal is to beat personal high scores.
- **Scoring System:** Scoring involves gathering points by crossing roads and collecting pizza slices. Players earn one point for every road crossed successfully and receive 10 points for each collected pizza slice. The primary objective is to achieve the highest score possible within the gameplay session.


## Game Mechanics

### Factories and Dynamic Generation

The game's infinite generation mechanic relies on 10 preset game objects serving as sections of road, which dynamically generate as the player progresses. This dynamic generation extends to cars and pizza within the game, which follow a similar mechanism. Utilizing factories for these elements enables the game to populate its environment dynamically as the player advances. Despawning of the roads is also implemented as the player passes to ensure an optimised experience.

### Input
- **Button Controls:** Menu navigation utilizes buttons, allowing players to interact with various options such as starting the game or accessing settings.
- **Swipe Gestures:** In-game movement is controlled by swipe gestures; players swipe in desired directions (forward, backward, left, or right) to maneuver the cat character, offering intuitive and responsive gameplay controls.

### Interactions with Characters and Environment
- **Main Character Interaction:** The main character, a cat in this game, is the primary focus. To prevent collisions with stationary objects like traffic cones or bins, raycasting is employed. This technique ensures that the cat doesn't walk into obstacles in the landscape. It detects if a collider is in the next tile and blocks movement to that tile if so.

- **Collectible Pizza Interaction:** The cat character interacts with pizza slices scattered across the game environment. Interacting with pizza earns the player 10 points, incentivizing players to collect these items during gameplay.

- **Collision with Cars:** Interaction between the cat and cars results in the end of the game. This emphasizes the need for players to avoid traffic obstacles so they can cross as many roads as possible.

### Camera Mechanics
- **Constant Movement:** The game features a continuously moving camera that progresses at a consistent pace. This mechanic adds urgency to gameplay, compelling players to keep pace and preventing them from lingering in one area for too long.

- **Player Tracking:** The camera is linked to the player's movement; if the player navigates swiftly, the camera catches up to maintain a suitable viewing position. This feature prevents the player from outpacing the camera, ensuring a clear view of the gameplay area. The camera will also track the player's X axis movements to ensure the player is never out of view.

- **Difficulty Tied Mechanism:** The camera's movement speed is directly associated with the chosen difficulty level. Higher difficulty settings result in faster camera movement, intensifying the gameplay experience and increasing the challenge for the player.


### Use of Defold's Messaging System
- **Structural Organization:** The game structure comprises the main collection which creates certain sub-collections: launcher, game, and death scenes, using collection proxies. Controlling all of this is the controller object located in the main collection, allowing for seamless communication and transitioning between these sections.

- **Inter-Scene Messaging:** Messaging plays a crucial role in transitioning between scenes. Messages such as 'show_main' or 'show_death' are utilized for smooth navigation between different sub-scenes, allowing for an uninterrupted flow of gameplay.

- **Player-GUI Interaction:** The GUI elements communicate with the player object and the controller using messages like 'score_increment' to update the score, maintaining a consistent and visible scoring system for the player.

- **Dynamic Object Configuration:** Upon the creation of new car objects, a 'set_variables' message is dispatched. This message is responsible for configuring essential variables like speed and direction for the newly spawned cars, contributing to varied and dynamic gameplay elements.

Defold's messaging system is crucial in managing scene transitions and critical interactions within the game. It handles seamless navigation between sub-scenes and controls essential elements like score updates ('score_increment' messages) and dynamic object configurations ('set_variables' messages). Further examples can be found in the scripts folder, such as triggering button-click sounds via messages.



## Game World
- The game presents a vibrant urban landscape with multitudes of horizontal roads, reminiscent of Crossy Road's setup. Cars continually traverse these roads, posing obstacles that players must avoid. The environment is rich with various obstacles, including barriers, cones, bins, fire hydrants, and more, scattered across the streets. The game offers a top-down view within a 2D sprite-based world, immersing players in a lively and challenging urban setting.
- The visual representation of the game world showcases a colorful and bustling cityscape, characterized by roads bustling with traffic and an array of obstacles strewn across the streets, creating an engaging and dynamic gameplay environment. Additionally, cars are accompanied by distinct engine sounds, with police cars featuring sirens that add an extra layer of urgency to the gameplay experience.


## Characters
- The game primarily focuses on the sole main character - an orange cat. This protagonist is depicted with several animations: an idle state where it calmly observes its surroundings and a jumping animation where it moves to another tile within the game.
- The character's backstory showcases that it is a stray city cat with a strong inclination towards searching for slices of pizza, thereby embarking on an intriguing and flavorful adventure.


## Mobile Game Design

- **General Design Principles for Mobile Games:** Mobile game design adheres to several core principles essential for handheld devices. Simple, intuitive controls are crucial for easy interactions, whether through touch, gestures, or other simplified inputs. Short play sessions are key, enabling players to engage in brief bursts of gameplay to avoid losing progress due to interruptions. A clear and intuitive save/load system is also crucial to facilitate seamless gaming experiences. Additionally, a user-friendly interface plays a pivotal role in mobile game design, ensuring accessibility across various screen sizes and enhancing overall user experience.
 
- **Comparison with Game's Design:** The game effectively incorporates numerous mobile design principles. Its gesture-based controls offer an immersive and intuitive experience, enabling seamless navigation and interaction. Short, fast-paced gameplay aligns with mobile design principles, ensuring that runs rarely extend for prolonged periods, allowing for quick re-engagement and progress. The emphasis on high scores seamlessly allows for this. Furthermore, the game's straightforward mechanics cater to the rapid pick-up-and-play nature commonly seen in mobile gaming experiences.


- **Suggestions for Mobile Suitability:** To increase suitability for mobile platforms, including more visual feedback into the game could enhance player engagement. Introducing elements that encourage social interaction or competition among players, such as leaderboards, might increase player retention and enjoyment. Also, implementing a dedicated tutorial section at the beginning of the game to familiarize players with the controls and mechanics can ensure a smoother experience.



## Monetization


- **In-Game Ads:** Implementing non-intrusive video or banner ads between game sessions or during specific intervals can generate revenue without affecting gameplay significantly. Ads can offer rewards or bonuses for viewing, such as revival after death, to incentivise players to watch them.
  
- **In-App Purchases:** Introduce microtransactions for cosmetic items such as different cats, or outfits for cats would be a viable source of income. Introducing microtransactions for additional lives or revivals upon death could also be a good plan for monetisation. These would have to be introduced carefully to ensure gameplay is not hindered.

- **Ad Removal Option:** Offer a premium version of the game without ads, either as a one-time purchase or a subscription model. This appeals to players who prefer an uninterrupted gaming experience.


## Distribution



- **Mainstream Distribution (iOS and Android App Stores):** Utilize the official iOS App Store and Google Play Store. These platforms offer extensive visibility, credibility, and ease of access for players to discover and download games securely.

- **Alternative Distribution (Indie Platforms):** Explore alternative app stores or indie platforms, which sometimes offer reduced fees for developers and flexibility in monetization strategies. Consider sideloading options or third-party app stores for potentially cheaper rates and varied monetization approaches.

- **Promotional Strategies:** Leverage social media platforms, gaming communities, and influencer marketing. Engaging in these channels can significantly enhance the game's visibility and attract a broader player base, positively impacting download rates.



