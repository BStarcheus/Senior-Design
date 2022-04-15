[< Back](../README.md)

# Coup RL

## Team Name
BTS

## Members
Brandon Starcheus - CS - starchbt@mail.uc.edu

## Faculty Advisor
Dr. Raj Bhatnagar - bhatnark@ucmail.uc.edu

## Project Area
Reinforcement Learning

## Abstract
Reinforcement learning has been applied to many games like Chess, Go, and Poker. Coup RL is an RL agent that learns to play the deception-based board game Coup with no prior knowledge. The agent was trained via self-play over millions of games, and showed significant improvement against human opponents.

## Problem Statement
Can we create a reinforcement learning agent that learns an optimal strategy that outperforms human opponents in a complex deception-based game? Can we understand how the agent learned to lie? How can these ideas be applied to other problem spaces?

## Existing Work on the Problem
While there has not be any work done specifically with the game Coup, there has been lots of work in reinforcement learning with other games of deceit like Poker and Skull. These games, however, have much simpler rules. We believe it will be interesting to analyze the learning in Coup because of the high risk high reward situations. Players can choose to lie on their turn as well as choose to call the bluff of other players on their turns. When a player is challenged they will lose a card if they were lying, but if they were not lying the challenger loses a card. While games like Poker have much simpler gameplay, we can still build on the existing work since the core RL concepts apply just the same.

## Applicable Background
- Self-studying reinforcement learning
- UC Coursework: AI, SWE, Python Programming, etc.
- Co-op work and personal projects in Python

## Approach
Coup can be played with up to 6 players in the original game, but for simplicity we will restrict this to 2 players for this project. At any point in the 2 player game, the state can be represented by:
- The number of coins each player has
- The pair of cards each player has
- Whether each of the cards is face down (known to the player but hidden from the opponent) or face up (elimintated)

Although the state space is quite large (about 0.5 million), we will approach the problem with traditional reinforcement learning without the use of neural networks. We plan to use Q Learning which stores Q values for each state action pair.

We plan to represent the game as an OpenAI Gym environment which will fully encapsulate the game and its rules. From there we can use this environment for both human opponents and self-play.

In order for the agent to play against human opponents, we will create a simple desktop app using PyQt.

The goal is to train the agent via self-play, and then compare its skill to humans with a game using the GUI. We can stop the agent at different points in training, play a game, and analyze the Q table to see how the agent is learning to lie.

For simplicity, in our initial attempt we will "break the rules" of the game and make the environment fully observable to the agent. Once this version of the game is working well, we can modify it to match the true rules where players can only see their own cards (partially observable).