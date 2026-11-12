## Prom Week: Designing past the game/story dilemma

Josh McCoy, Mike Treanor, Ben Samuel, Aaron A. Reed, Michael Mateas, Noah Wardrip-Fruin University of California Santa Cruz, Expressive Intelligence Studio

1156 High Street

Santa Cruz, CA 95064

{mccoyjo, mtreanor, bsamuel, aareed, michaelm, nwf}@soe.ucsc.edu

quest flags and conversation trees to further the plot or advance character development [2]. One side effect of these operational logics is that moments of character development and incidental story that could theoretically happen at any point in the game's narrative are restricted to specific moments. For example, in all three entries of the Mass Effect series, meaningful conversations that alter the relationship between the player character and their squad mates are limited to specific locations at pre-defined times in the overall arc of gameplay. Another issue that arises from relying on quest flags and dialogue trees is the creation of a tremendous authoring burden; additional player agency comes at the price of exponentially more content, as the game designers must account for every potential path a player may take through the game's narrative. This leads to either large authoring teams, such as the Star Wars MMORPG The Old Republic's cadre of 12 writers that were employed full time for years before the game reached preproduction [3], or story games that provide the user with minimal control over how the narrative unfolds, a design pattern called "beads on a string" [4]. The former solution is untenable, the later undesirable.

Conversely, games such as The Sims 3 [5] excel along the interactive dimension by giving players significant control to develop a social space between the characters. This sandbox style of gameplay can feel highly dynamic to players. However, the characters themselves are largely empty vessels through which the player acts, usually speaking with abstract thought bubbles or sounds rather than natural language. Narrative is represented in a very limited way (e.g., simple character aspirations) with few fictionally-presented consequences.

When the player interprets the events in a complicated system as a narrative, an intensely rewarding and engaging experience can result [6-8]. Many games such as The Elder Scrolls V: Skyrim [9] feature narratively charged open worlds with a great degree of player freedom and many possible emergent stories. However, these games can only rarely react in meaningful ways to the emotional or social consequences of player decisions. This is because these dimensions of narrative are usually not simulated by these games. The player can make their own interpretations about these dimensions but the system is unable to represent or reason over this crucial part of a compelling narrative. The social and emotional world is invisible to the game system. If we could capture the enjoyable aspects of player-driven narratives while still keeping the complex dynamism of sandbox games, we could enable a new type of game experience that is both deeply responsive to player choice and also personally meaningful.

For Prom Week, creating the experience we imagined required fundamental technical research to enable new kinds of authorial affordances. When the only narrative operational logics afforded to the developer of a storytelling game are quest flags and dialogue trees, it is difficult to carve out new areas of game design space that have not already been explored by previous games

## ABSTRACT

New player experiences require new game designs - and some designs only become possible with new technology. Emergent narratives are part of existing story games but the game systems are not capable of understanding the stories their players create. If we could capture the enjoyable aspects of player-driven narratives while still keeping the complex dynamism of sandbox games, we could enable a new type of game experience. Creating this experience would require fundamental technical research to enable new kinds of authorial affordances.

This paper presents the lessons learned while designing the game Prom Week and AI system Comme il Faut together to produce such an experience - a two and a half year process of researchdriven game design. Prom Week tightly combines player experiences of choice and consequence (as found, for example, in simulation games and combat systems) with experiences of specific characters, histories, language, and narrative conclusions (as found in the non-interactive, or minimally-interactive, fictions of many games). This combination was accomplished by creating novel technology informed by the design problem, experimenting with gameplay approaches appropriate to the technology, iterating on both using player feedback, and finally executing a unique design providing satisfying stories that reflect the player's choices in a wide possibility space.

## Categories and Subject Descriptors

K.8.0 [Personal Computing]: General - Games. I.2.4 [Artificial Intelligence]: Knowledge Representation Formalism and Methods - Representations (procedural and rule-based).

## General Terms

Design

## Keywords

Game design, social simulation

## 1. INTRODUCTION

A recurring theme in game design theory is the tension between gameplay/interactivity and narrative. The narrative dimension is best embodied by "storytelling games," which feature rich plots, memorable characters, and stories that engage players on an emotional level. Mass Effect [1] is an example of a storytelling game. Many storytelling games rely on the operational logics of using the same tools. Similarly, simulation games rarely offer the authorial leverage or character performance necessary tell a meaningful story. New affordances shape how authors can view story game problems and solutions, and make new types of games possible to conceive and create.

We strongly believe that simply designing a new AI system is not an adequate exploration of such fundamental questions. The only way to understand if a design and/or technology solution will enable a new player experience is to build a game and put it in front of players. To test this idea, we created a playable model of social interaction, Comme il Faut (CiF) [10], and a fully realized game designed around and in conjunction with it, Prom Week [11]. We believe with this work we have taken a significant step towards enabling playable stories that are emergent but also can be shaped by a computational model of social interaction.

This paper presents a survey of the lessons learned while designing a game and AI system together to produce such an experience. One such insight was the emergence of a new form of gameplay, the social physics puzzle, which was only enabled through the design process of integrating the affordances of an AI system with game mechanics. By using an AI-driven design process we were able to iterate both game and system in ways necessary to explore a new design space. Additionally we informally evaluate the success of Prom Week in creating unique and playable narrative experiences using both qualitative and quantitative analysis.

## 2. PROM WEEK

A broad overview of Prom Week has previously been written [12], but we briefly summarize the game here as well. Gameplay in Prom Week revolves around the social lives of eighteen characters. In any given "Story," or campaign, the player is given a set of goals to complete during the week before the prom. For example, in Zack's Story, one goal is to get him a prom date. Goals can be satisfied through an open-ended set of solutions discovered through interaction with the characters and social state. For example, the player could have Zack form a friendship with a popular character over a shared interest, or exploit another character's trait of "competitive" to make an enemy when Zack flirts with someone the competitive character has a crush on.

The player works toward goals by choosing social exchanges for each character to initiate (Figure 1). Social exchanges are multicharacter social interactions that modify the social state connected to the participants. Which social exchanges are available and how each changes the social state is managed by the game's AI system, Comme il Faut (CiF) [10]. The player chooses from the top social exchanges that each character desires to play with each other character. CiF provides this ordered list based on its character models and the current social state.

Figure 1. Prom Week's user interface. On the left are the social exchanges Doug wants to initiate with Chloe, including Share Interest and Pick-Up Line. The thought bubbles show a glimpse of the characters' opinions of each other; Chloe thinks Doug is her best friend and idol, while Doug feels similarly, but less strongly, toward her.

<!-- image -->

In addition to determining what exchanges characters want to perform with each other, the system also determines whether a responding character will accept or reject a proposed social change, and selects a scene to best perform that decision from a large library of alternatives. Figure 2 shows an excerpt from a social exchange where Zack asks Monica on a date and Monica rejects him because he isn't popular. Each factor in this scene (Zack's desire to ask Monica out, her decision to reject him, and her reasons for doing so) are all part of the underlying social simulation rather than pre-decided, static story content.

Figure 2. An excerpt from a social exchange where Zack tries to ask out someone out who is out of his league. Her rejection reflects her cold and honest personality.

<!-- image -->

While goals usually pertain to specific characters, players take on the role of an external observer and manipulator who can select a social action for any character to initiate. For example, to remedy the situation in Figure 2, the player might try to make Zack popular, by getting him more friends, performing actions categorized as cool, etc. Or the player can try to make Monica no longer popular, by having her do embarrassing things, cut ties with her popular friends, etc.

Because the gameplay of Prom Week involves manipulating the social space, which is the primary story content of the kind of high school narrative we wanted to emulate, the gameplay is the story. Every action the player takes advances the game's narrative and sends ripples throughout the internal social state, which in turn affects which actions are available in subsequent turns. The system is a partner of the player, giving the narrative meaning and shape. This is in contrast to a sandbox game in which gameplay may be the story, but the story is formed only in the mind of the player, and not understood or reasoned over by the system. While CiF-enabled stories are authored in the sense that the designers create the initial situation, define the goals for each scenario, and create a pool of templated scenes for characters to perform, CiF enables emergent solutions to each social puzzle, making the resulting story space highly dynamic and responsive to player action.

## 2.1 Stories

Prom Week provided unique opportunities for us to innovate in the design of emergent story-based puzzles. Social physics puzzles could easily have conflicted with our desire to tell coherent and satisfying stories. The structure of the game's final levels and goals was designed to address these potential conflicts.

A player of Prom Week begins by selecting a story. A story is a collection of levels, each representing a specific time and place in the week before the prom, where the player can take social actions involving a particular subset of the characters in the story. In addition to getting Zack a date, some other example goals include ending Zack's war against a popular bully, or getting Zack into a relationship with someone "popular." Goals in a story are sometimes designed to be complementary: ending a rivalry with a popular bully could improve Zack's relations with the popular crowd, which could help his other goals. As mentioned above, objectives can be met in a variety of ways: the player could forge a friendship between Zack and the bully, or perhaps make the bully lose his social standing, which might change his antagonism towards Zack.

Every story's last level takes place at the prom. After the player runs out of turns, or decides to skip to the end of the night, a customized ending is presented that reflects the combination of goals achieved. For example, Zack's story might happily end with him becoming the prom king if the player was able to get him to date a popular person. Or, if the player had him abandon his unpopular friends to reach this goal, he might get a bittersweet ending where he still becomes prom king, but is confronted by his old friends. Every story has many possible endings for various combinations of goals the player might have completed. As the player finds more endings, additional stories are unlocked. In addition to the explicit rewards of endings and new stories, players are free to define their own criteria for play and success, such as creating particularly awkward or humorous situations, recreating events from their own lives, or trying to solve each level's social puzzles in as few moves as possible.

## 2.2 Social Physics

Prom Week allows players to solve goals flexibly, while maintaining consistent and believable characters. CiF enables a style of gameplay we call social physics [12]. While video games have achieved a high level of playability in physical spaces, with activities like combat, movement, and physics-based environmental manipulation all well-explored, Prom Week set out to make social spaces as playable as physical spaces. The goal was not to recreate the everyday social world, but to create social dynamics specifically crafted for a targeted experience - just as platforming games don't reproduce the physics of the everyday world, but rather an enjoyable simplification tuned for gameplay, and fiction writers portray behavior and dialogue in stylized fashions that differ markedly from typical conversation.

Without a system like CiF, representing social interactions between any two characters in our story that takes into account cultural context, personal history, and current relationships would be impractical, or perhaps impossible. The space of contexts (states of the virtual world) and social interactions (player interactions) is prohibitively large and not amenable to brute-force authoring. CiF provides knowledge representation and processes that model social interactions to make this ambitious goal tractable to implement.

Prom Week's social physics is based on a set of over 5,000 sociocultural considerations. The considerations were crafted based on ethnographic analysis of pertinent media sources [13]. As this type of analysis captures a snapshot of social norms and behaviors in a particular cultural setting, any social biases, stereotypes or other patterns of social interaction may also be encoded. The encoding is not an accident, but a deliberate authoring strategy, one aimed at producing a consideration of human values through gameplay [14]. In particular, Prom Week preserves certain biases from high school media for two purposes. First, to bootstrap player understanding of the social world. Second, as the consequences of these biases play out in the game, to prompt new kinds of reflections (in combination with incommensurable character goals and goal-specific endings, which make it clear that game direction and strategy are not preordained, but products of player choice). At the same time, other biases from media were deliberately omitted or inverted, such as many gender and heteronormative biases. These serve complementary functions: producing challenge and surprise as players come to recognize their absence, and reflection on what may previously have been taken for granted.

These considerations are the rules that influence the characters' desires, each adding either a positive or negative numerical weight to the desirability of each potential social exchange. One example of a rule in natural language might be this: a character who is vengeful (a static trait) will be more likely to do something mean to someone who has recently done something mean to them. A more complex example: a character might be more likely to do something romantic with someone who was recently mean to the person who was mean to them ("the knight in shining armor"). These rules encode a notion of "social common sense" which is what the player will reason over while striving to satisfy each level's goal.

After several design iterations, we decided on the following components as the basis of Prom Week's simulation of social state as the ones that let us best capture the kinds of social interactions we waned to simulate:

Relationships: binary, reciprocal and public connections between characters. The three relationships in Prom Week are: friends, dating and enemies.

Social Networks: scalar, non-reciprocal and private feelings from one character toward another. The three networks are: buddy, romance and cool.

Statuses: temporary feelings, either unitary or directional, that are often consequences of social interactions. Some statuses, such as embarrassed, are internal feelings. Other statuses and represent social standing, for example, being popular.

Traits: permanent attributes of a character's personality. Most traits are private, such as being competitive, while others are public knowledge, such as being a sex magnet.

Social Fact Database: the social history of interactions between characters. All entries in the social fact database are public knowledge and thus comprise the characters' collective social history.

Cultural Knowledge Base: the objects of the social world, a zeitgeist of popular opinion about each object, and each character's personal relationship to that object, which can be likes, dislikes, wants, or has. For example, Zack may like and want a scientific calculator even though they are generally considered lame.

The following example illustrates how the structures described above constitute a social state.

Simon is a character with the traits helpful and witty. Naomi is a character with the trait attractive. Simon has the status of has a crush on Naomi, and Naomi has the status of popular. Naomi and Simon have the relationship of being friends. Simon has a high romance network value toward Naomi but she has a very low romance network value towards him. Naomi also has a low cool network value toward Simon. All other network values are neutral. The cultural knowledge base states that both Simon and Naomi like scientific calculators, which are lame, and footballs, which are cool. In the social fact database is a past action Simon took towards Naomi marked as embarrassing, labeled as "Simon misunderstood Naomi asking for help on homework as a romantic advance."

Given a social state, CiF operates by looping through a set of processes to determine what characters are interested in doing, and how they might respond to the other characters taking these social actions with them. The first process is desire formation. This process determines a character's volition (or will) to play a social game with other characters. Every time desire formation is executed, every character determines their volition to play every social game with every other character. Volition is scored by counting the weight of many individual rules that encode the social concerns of the story world. After this process, all characters in the cast have a volition value for every social game with regards to every other character.

Next, the player selects a social exchange for one character to perform with a second. Social exchanges have an initiator intent (the initiating character's desired social change, such as to start dating) and three roles: an initiator, a responder, and a possible third party. When the player selects a social exchange, basic information about how the initiator and responder relate to one another is displayed. If a third party is involved, CiF selects the character for whom the most influence rules pertaining to a third party were true. (For instance, in the Spread Rumors social exchange, a third party who neither character likes is selected.)

Once an exchange is chosen, CiF determines how the responder reacts based on the social context. This process is very similar to scoring volition for initiators: a sum is calculated for true rules that pertain to responding to the social exchange. If the sum is zero or greater, the game responder accepts the intent of the game. Otherwise it is rejected.

While each social exchange has a primary result for success (such as changing the dating relationship to true for an accepted Ask Out between two characters), the system includes a large number of scenes narrating different ways an exchange can play out, based on the social state of the participants and whether the exchange was accepted or rejected. These are called effects. For example, if a character plays Share Interest with another character, and the exchange is accepted, there could be an effect specific to situations in which the two characters both like a "cool" object in the cultural knowledge base, or another in which they bond over a "lame" object, celebrating their deviation from the will of the zeitgeist.

Each effect is associated with a performance realization instantiation. An instantiation is a set of template-based dialogue acts and associated animations. After the instantiation is realized, the social state change associated with the chosen effect is applied. This includes placing an entry into the social facts database to account for the exchange, to be referenced and considered in all future social exchanges.

The last step is running a set of "trigger rules" over the new social state. Trigger rules account for social changes that result from multiple social exchanges and other elements of the social state. For example, a character will receive the status of "cheating" after starting a relationship with one character when they are already dating someone else.

## 3. The Design Process and Challenges

The impetus for creating Prom Week was to create a compelling game experience around the social AI system CiF, and the entire game was designed with this system in mind. This methodology, called AI-based game design [15] or expressive AI [16], fundamentally changes the concerns of typical design: instead of thinking of design choices and game mechanics in terms of what existing conventional systems can do, the primary criteria for design becomes creating a game that best leverages the power of a novel system. In this case, CiF is the AI system around which the design was centered, so the changing social situations of virtual characters brought about through game play were the primary concern.

As AI-based game design is distinctly different from other game design methodologies, it has the potential to create new types of video games. The space of all possible video game designs is considerably larger than the fraction which has been explored to date. A research-centered approach has the potential to lead to unexplored design spaces. AI-based design raises the priority of technological innovation to the same level of the game design itself. In other words, with new technological abilities, new types of games can be imagined.

A benefit of AI-based game design is that the processes of designing of the game, authoring content for it, and refining the AI system each inform one another (figure 3) [17]. The act of designing game mechanics to be used in conjunction with an AI system tests the system. By exploring and determining the affordances the AI provides (or fails to provide) for gameplay, the designer exposes the weaknesses and strengths of the AI in for CiF

Figure 4. The computationally assisted paper prototype Figure 3. The AI-based game design process. Creating new AI systems, such as CiF, provide new affordances in the space of Game Design, while implementing AI in a game, such as Prom Week, offers new context for expansion on the AI itself.

<!-- image -->

modeling its domain, which can be used to further improve it. As the AI continues to evolve, it in turn suggests different game design possibilities. This cycle of iterative refinement of both AI system and game improves the design and functionality of both systems: the AI becomes better at modeling its domain while the game becomes both a better gameplay experience and better at providing play in its domain. This process of creating a fullyplayable game based on an AI system is potentially very beneficial to developers of AI in areas such as story generation, natural language generation, and social or psychological modeling. Creating a full game with this methodology allows for many more cycles of iteration and refinement on the underlying systems, enabling a richer final product that a system developed in isolation or with only a system demo as a demonstrator.

The following section will demonstrate how CiF and Prom Week developed together over the course of its two and a half year development.

## 3.1 Assisted Paper Prototype of Prom Week 1.0

Prom Week (and I [18]) was first implemented as a paper prototype with a computational assistant (Figure 4). This goal of this version of Prom Week was to represent and reason over compelling social situations along with the variations of the resultant behavior that arise from different personalities being placed in similar roles. The prototype had the player choose to side with one of two high school factions (Goths or Emos) and help that faction win the favor of the student in charge of the audio equipment at the prom, Milton. Characters with personality descriptions taken from Reiss' motivational analysis [19] were present as stand-up models and character sheets. The player was dealt a hand of cards (each listed with basic needs effects) and was able to play them on the characters. After cards were played on characters, the game master would enter the cards' effects in the computational assistant, which would then determine which social exchanges would be initiated by the characters. If the social exchange resulted in behavior in line with Milton's personality, a token would go to the faction of the character who initiated the social exchange. After 10 rounds of game play, the faction with the most tokens would gain Milton's favor and control of the playlist for the evening.

As this prototype was the first incarnation of a playable form of CiF, this design space was highly malleable and resulted in sweeping changes to our preconceptions of what a game in the space of social play could be. Through the development process and playtesting, we discovered that social exchanges solely driven by psychological needs were unintuitive and hard to communicate or justify to players. Particularly, the abstracted social exchanges performed by the characters did not match the exchanges that were anticipated by the playtesters given the characters' basic needs. Motivated by this, the next iteration of Prom Week shifted its focus to the logic of social statuses and relationships between characters.

Figure 4. The computationally assisted paper prototype for Prom Week

<!-- image -->

Realizing that creating an AI system to be used as the core of a video game requires a different frame of thinking than implementing a model "correctly" was an important step in our process. Our direct, straightforward implementations of complex topics, such as our basic needs modeling from motivational analysis, did not capture the depth of social play we were hoping to capture; a few vectors of scalar values with a small amount of conditional logic did not provide a compelling game experience and proved to neglect the aspects of social state that players tended to reason over, the social context. Instead of exposing the engineering choices as game mechanics, we decided to base the affordances given to the player on what our players were thinking when they played the game.

## 3.2 Promacolypse Demo

The version of Prom Week presented at Game Developers' Conference 2010 [20], titled Promacolypse (figure 5), comprises Prom Week's second iteration. The version of CiF used in Promacolypse was a redesign focused much more on the social space around the entire cast of characters and not focused on individual characters and their psychological needs. We also abandoned the idea of antithetical ways, or ways that are not in keeping with the conventions of a social exchange, to play social exchanges stemming from Berne's transactional analysis [21]. These antithetical ways of playing social games flipped the intent of the social game on its head which resulted in unpredictable agent behavior and confused players. This demo was completely computational and consisted of many of the same processes and data structures described in the preceeding sections: social networks, statuses, CKB (cultural knowledge base), SFDB (social facts database), and triggers were all added to CiF to support the new design decisions as well as facilitate making the previouslypaper parts of the game computational.

With such large changes made to the AI system, many new options of game design presented themselves. While the game was still character-based, the goal of the game became to reach certain social states through making the characters play social exchanges with one another (as opposed to the previous paradigm of playing cards consistent with characters' basic psychological needs). With the exclusion of antithetical social exchange outcomes, characters needed a way to respond to the intent of an exchange; if the initiator started a flirtatious exchange with someone who had low romance with them, the system needed a way to factor the responder's social situation into the outcome of the exchange. To achieve this, antithetical social game outcomes were replaced with accept/reject logic that is deeply tied to the social state existing among the characters.

Figure 5. A screenshot of Promacolypse demo that demonstrated the early "social context" based version of Prom Week

<!-- image -->

While authoring content for the Promacolypse demo, consisting of social games and their instantiations, we found that we were building a lot of common sense about social behavior into the rules for each social exchange. This repetition of rule writing revealed the need for constructing a mechanism of general social reasoning that would encompass the concerns of many social exchanges. To address this, we developed the structures we call microtheories to capture the social knowledge of how to act within the context of a particular social framework (such as a friendship, or towards someone you think is cool).

With social exchanges each having an intent, a large set of microtheories with rules to influence a character's desire to perform that exchange, and the ability of characters to accept or reject a proposed exchange, social exchange authoring could focus on what makes a particular exchange a unique act within the system. For example, the exchanges Share Interest and Reminisce both have the intent to raise another character's buddy network value toward the initiator. In general, if two characters are friends, the friend microtheory will increase a character's desire to play exchanges with this intent. However, if the two characters share an interest in an item from the cultural knowledge base, for example, we can write rules making the initiating character more likely to play Share Interest. Likewise, if the two characters have a positive history of social interaction, the initiator might instead want to play Reminisce. Such exchange-specific rules are now the only ones embedded in each social game, leaving general rules to the domain of the microtheories. These changes dramatically reduced authoring time.

## 3.3 Beta Version

Playtesting the Promacolypse demo brought to light several needed improvements to the games design and AI system based on data from players. The first was that the game needed more narrative structure. This led to the addition of the story progression, level, and ending structure described above. Another change came from players' frequent desires to solve problems using a third character in addition to the initiator and responder. To support this, the beta version added third party social exchanges that can be initiated by the player.

Figure 6. A screenshot that shows the beta version of Prom Week. The yellow bar on the left shows the social influence points.

<!-- image -->

The players were often confused by the outcomes of social exchanges played in the demo. They asked questions like "why did that happen?", "why did the initiator want to do that to that person?", or "why did the responder act that way?" We needed to expose the reasoning done by CiF in a way that added to the game experience. We decided to present this information in an abstracted form, and erred on the side of providing too much detail, giving the player the ability to dig into the interface to learn the details of what was happening within CiF (figure 6).

As refinement and playtesting continued, another concern became evident: the game was too hard. With such a complex simulation, the results of any given social exchange, while believable, were often unpredictable. For example, while the interface might have indicated that two characters liked each other, an attempt to make them become friends with the Make Plans exchange might fail, perhaps because of the responder's trait of shy, or a long-ago event in the social facts database where a friend of the initiator's did something mean to the responder. While these cases demonstrate exactly the sort of complex social intelligence we wanted to give to characters, they were not always apparent (or fun) for players. Because of this, we introduced a new game play mechanic called social influence points (SIP). SIP allows players to know more about and change how characters will respond to a social exchange before it is played. SIP is a limited resource that is increased when an unmodified social exchange is used, and decreased when the player either reveals if a character will accept or reject a social exchange, changes a reject into an accept or vice versa, reveals all of the motives for why a character will respond, or forces an initiating character to select a social exchange that is not one of his top five priorities. With SIP, players can complete goals much more easily because they can carefully choose which social exchanges really must succeed to make progress towards a particular goal, and players can "nudge" the fictional world in directions they find more interesting without turning the characters into puppets. Making SIP a limited resource ensured that the majority of player choices were still governed primarily by CiF's simulation.

## 3.4 Final Version

The most common pieces of feedback from the beta were that the game was still too hard and that the interface was too complicated. To address the first problem, we had to reevaluate the sort of goals we were asking players to complete. The level of detail of the simulation, together with the difficulty of clearly communicating the many parts of the system and their effect on characters' actions, was still making it hard for players to reliably get the characters into a desired social state (even with SIP). For example, some goals were stated in the form of information easily visible to the player (such as making two characters enemies), while others were based on information not exposed by the interface (such as becoming embarrassed, or acquiring a history of a certain type of behavior). To fix this, we modified all goals to match closely to the most obvious social exchange intent types, so the player could more easily see the relevant parts of the social state and determine what actions to take to change it.

To address the second concern, the final version of Prom Week had a completely redesigned interface that did a better job of fictionalizing the interface elements. Rather than presenting most social state information in menus or abstract information bars, these details were presented as if they were the thoughts of the characters. We have found that by tapping into concepts that players are familiar with (such as media conventions and their own thinking about their social world) the game play experience feels less technical and thus easier for most to digest (Figure 1).

## 4. EVALUATION

While there are potentially many ways to evaluate a game like Prom Week, our first evaluation focused on a quantitative analysis of user generated gameplay traces. We also present a qualitative look at its reception through awards and reviews. Note that the evaluation presented in this paper is only of popular reception and gameplay traces. A more rigorous evaluation of how well Prom Week fulfilled its design goals is future work. Furthermore, developing a method to evaluate the perceived social and narrative qualities of an interactive experience is itself a novel research contribution.

## 4.1 Gameplay Trace Analysis

As users complete levels in Prom Week, we silently capture the social exchanges chosen during each turn of the game, anonymize player-centric identification, and store the resulting file on a server. Each of these files is a single gameplay trace. Level lengths in Prom Week are fixed, varying between ten and twenty turns. Gameplay traces offer a very objective view into how users are interacting with the system, so analyzing them can be a good way to verify if a system is enabling the desired means of interaction.

We analyzed 5,425 gameplay trace files, generated in a three month period between our initial release of February 14 th and May 17 th 2012. This count does not contain traces for partially completed levels, nor traces generated from tutorials.

As mentioned above, one of the primary goals of Prom Week is to advance the medium of interactive narrative by increasing player agency at the story level. One method to measure this agency is to gauge how personal an experience a playthrough of Prom Week is for any given player; ideally, every player's path through the story would be unique. Conversely, if there is significant overlap between multiple players' traces, it implies that either the story structure of the game is largely fixed and players are merely traveling down a pre-defined path, or that certain paths are clearly

## Average Path Visitation Per Time

Figure 7. This plot shows how unique each player's path through the story space is as time progresses. The x-axis is the time, or number of turns, and the y-axis the average of how many times a story path has been visited.

<!-- image -->

more desirable than others, obviating the pleasure of choice central to interactive storytelling.

Figure 7 is a view into how distinct players' play traces are from each other in Prom Week. The different lines represent six different stories from the game. The X axis represents the current turn of the campaign, and the Y axis represents the average of how many different story traces had traversed the same path. For example, of the 390 gameplay traces that represent the first level of Oswald's story, on the first turn there is no variation in path traversal, because campaigns always begin with a default start state. However, across all 390 playthroughs, players chose a total of twenty-five different social exchanges for the first turn. This means at this point there exist twenty-five different story branches, each of which is experienced by an average of 15.6 players. At the third turn, there are a total of 307 different branches that have been created, which means that any given branch is experienced by an average of 1.27 players. On turn four, the average drops to 1.07. While the average never hits one exactly, since all players begin in the same starting state, in only three turns players are experiencing content in a sequence that has never been seen before. Figure 7 shows that similar trends exist for each of the game's campaigns.

This is one indicator that Prom Week successfully met its goal of offering a large degree of variability to players. This variability could not have been produced without the large branching factor of the game's narrative, which in turn could not have been produced without the radically different approach to authoring and design that our novel AI system enabled.

## 4.2 Critical Reception

Even though Prom Week permits players to shape their own stories, analyzing game traces fails to convey how satisfying those stories may or may not have been. To address this informally in a qualitative sense, we turn to some of the critical reception and reviews Prom Week has received since its release.

Several trusted sources of video game news and reviews have spoken on both the technical and emotional achievements of Prom Week. Game news site Rock Paper Shotgun's reporter confessed that "After the grim social strategies I'd been considering, did I deserve to be Prom King? … now I feel bad and impressed, and want to play it all over again." Play This Thing called Prom Week "… a notable advance in the state of the art of interactive narrative design." Alastair Stephens says that "… like all successful stories, [Prom Week] swiftly moves beyond the mechanical, beyond the ludic, to the personal and emotional."

Prom Week garnered recognition in competitive settings as well. It was selected as a finalist in the 2012 Independent Games Festival in the category of Technical Excellence, and was also a finalist at the 2012 IndieCade festival.

It can be difficult to measure the impact a game leaves on its audience. However, early quantitative and qualitative analysis suggests Prom Week has successfully employed innovative technology that enables previously unexplored forms of gameplay and interactive narrative. Players have unique experiences that are driven by story and character and which can produce emotional, meaningful responses in their audience.

## 5. CONCLUSION

This paper presents a survey of the lessons learned while designing a game and AI system together to produce such an experience. This paper details many insights garnered through the design process including the emergence of a new form of gameplay, the social physics puzzle, which was only enabled through the design process of integrating the affordances of an AI system with game mechanics. An AI-driven design process allowed us to iterate on both the game and system in ways necessary to explore a new design space. Additionally we evaluate the success of Prom Week in creating unique and playable narrative experiences using both qualitative and quantitative analysis.

## 6. REFERENCES

- [1] BioWare, "Mass Effect." Microsoft Game Studios, 2007.
- [2] M. Mateas and N. Wardrip-Fruin, "Defining Operational Logics," in Digital Games Research Association (DiGRA), 2009.
- [3] K. Orland, "'Old Republic' writer discusses '60 manyears' of work," NBC News, 2011. .
- [4] G. Costikyan, "Games, Storytelling, and Breaking the String," in First Person: New Media as Story, Performance, and Game, MIT Press, 2008.
- [5] "The Sims Studio", "The Sims 3." Electronic Arts, 2009.
- [6] R. Burkinshaw, "Alice and Kev: The Story of Being Homeless in The Sims 3." 2009.
- [7] T. Francis, "The Minecraft Experiment, day 1: Chasing Waterfalls," PC Gamer2, 2010. [Online]. Available: http://www.pcgamer.com/2010/11/20/the-minecraftexperiment-day-1-chasing-waterfalls/.
- [8] M. Fahey, "Bring Us Your True Tales of Skyrim Adventure," Kotaku, 2011. [Online]. Available: http://kotaku.com/5858653/bring-us-your-true-tales-ofskyrim-adventure. [Accessed: 18-Mar-2013].
- [9] B. G. Studios, "The Elder Scrolls V: Skyrim." Bethesda Softworks, 2011.
- [10] J. McCoy, M. Treanor, B. Samuel, N. Wardrip-Fruin, and M. Mateas, "Comme il Faut: A System for Authoring Playable Social Models," in Artificial Intelligence and Interactive Digital Entertainment, 2011.
- [11] J. McCoy, M. Treanor, B. Samuel, A. Reed, N. Wardripfruin, and M. Mateas, "Prom Week." Center for Games and Playable Media, 2012.
- [12] J. McCoy, M. Treanor, B. Samuel, A. Reed, N. WardripFruin, and M. Mateas, "Prom Week: Social Physics as Gameplay," in The Foundations of Digital Games Conference, 2011.
- [13] J. McCoy, "All the World's a Stage: A Playable Model of Social Interaction Inspired by Dramaturgical Analysis," University of California Santa Cruz, 2012.
- [14] M. Flanagan, D. C. Howe, and H. Nissenbaum, "Values at play," in Proceedings of the SIGCHI conference on Human factors in computing systems - CHI '05, 2005, p. 751.
- [15] M. P. Eladhari and M. Mateas, "Semi-autonomous avatars in world of minds," Proceedings of the 2008 International Conference in Advances on Computer Entertainment Technology - ACE '08, p. 201, 2008.
- [16] M. Mateas, "Expressive AI: A Hybrid Art and Science Practice," Leonardo: Journal of the International Society for Arts, Sciences, and Technology, vol. 34, no. 2, pp. 147-153, Apr. 2001.
- [17] G. Smith, A. Othenin-Girard, J. Whitehead, and N. Wardrip-Fruin, "PCG-Based Game Design: Creating Endless Web," in Foundations of Digital Games Conference (FDG 2012), 2012.
- [18] J. McCoy, M. Mateas, and N. Wardrip-fruin, "Comme il Faut : A System for Simulating Social Games Between Autonomous Characters," in Proccedings of the 8th Digital Art and Culture Confernce (DAC 2009), 2009.
- [19] S. Reiss, The Normal Personality. Cambridge, MA: Cambridge University Press.
- [20] J. Lowensohn, "GDC: What's next for video game AI?," Web Crawler - CNET News, 2010. .
- [21] E. Berne, Games People Play: The Basic Handbook of Transactional Analysis, Seventh Im. New York: Ballantine Books, 1964.