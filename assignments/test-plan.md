[< Back](../README.md)

# Test Plan

## Overview
Coup RL consists of several submodules, each with different necessary levels and methods of testing. The basic game logic for Coup found in the gym-coup environment will have unit and integration tests to validate the behavior of the game and gym environment. The desktop app will also have unit and integration tests to validate the functionality of the UI, its connection to the underlying gym-coup instance, and its use of the reinforcement learning agent. Finally, the RL agent will have its base functionalities tested. The agent's improvement over many games via manual training and self-play will also need to be tested, but due to the nature of the tests those have been omitted from this document.

## Test Cases
### Game Logic and Gym Environment
1. Game Logic Unit Test
    - ID: GLUT
    - Purpose: Validate the game's configuration and each action a player can take.
    - Description: Validate the game is configured correctly given object initializations. Validate the game's configurations change correctly after given action functions are called.
    - Inputs: Game objects, actions
    - Outputs: Game objects with state correctly modified for given actions
    - Normal
    - Whitebox
    - Functional
    - Unit

2. CoupEnv Integration Test
    - ID: CIT
    - Purpose: Validate the gym environment and its use of the game logic.
    - Description: Test the standard gym functions and validate the state of the game has changed correctly. Validate that the correct list of valid actions is being returned for a given game state.
    - Inputs: CoupEnv objects
    - Outputs: CoupEnv objects with internal game state correctly modified, valid list of actions for given state
    - Normal
    - Whitebox
    - Functional
    - Integration

3. CoupEnv RL Interfaces Test
    - ID: CRIT
    - Purpose: Validate the data that will be returned to the RL agent.
    - Description: Validate the observations and rewards being output for given game states and actions.
    - Inputs: CoupEnv objects
    - Outputs: Observations and rewards for given states and actions
    - Normal
    - Whitebox
    - Functional
    - Integration

### Desktop App
4. App Unit Test
    - ID: AUT
    - Purpose: Test all components that have no dependency on the underlying gym-coup instance.
    - Description: Validate the menu and navigation work correctly using automated GUI tests in PyQt.
    - Inputs: Desktop app
    - Outputs: Pass for valid reactions to UI component interaction
    - Normal
    - Blackbox
    - Functional
    - Unit

5. App Game Initialization Test
    - ID: AGIT
    - Purpose: Test initialization of the game using the menu options.
    - Description: Test different inputs from the menu and verify the underlying game and RL setup are configured correctly.
    - Inputs: Desktop app, menu configurations
    - Outputs: Desktop app with CoupEnv and RL agent correctly initialized
    - Normal
    - Whitebox
    - Functional
    - Integration

6. App General Actions Test
    - ID: AGAT
    - Purpose: Test the action buttons.
    - Description: For each action button, verify that the game board is correctly updated given the previous game state.
    - Inputs: Desktop app, game state
    - Outputs: Desktop app with board updated
    - Normal
    - Blackbox
    - Functional
    - Integration

7. App Card Actions Test
    - ID: ACAT
    - Purpose: Test actions where the user selects cards.
    - Description: For each type of card selection action, verify that the game board is correctly updated.
    - Inputs: Desktop app, game state
    - Outputs: Desktop app with board updated
    - Normal
    - Blackbox
    - Functional
    - Integration

8. App Agent Integration Test
    - ID: AAIT
    - Purpose: Test the app's ability to load, train, and save RL agents.
    - Description: Test the app for playing with different RL agents from files. Verify it is loaded correctly, and saves the updated agent to the file after the game. Also test with invalid agent files.
    - Inputs: Desktop app, RL agent
    - Outputs: Desktop app with loaded agent, saved agent data after game
    - Normal
    - Whitebox
    - Functional
    - Integration

### Reinforcement Learning Agent
9. Agent Configuration Unit Test
    - ID: ACUT
    - Purpose: Test the RL agent support code to load and save agent data.
    - Description: Test loading previous RL agents saved to files, and creating/updating new agent files. Also test loading invalid agent files.
    - Inputs: RL agent file
    - Outputs: Updated RL agent file
    - Normal
    - Whitebox
    - Functional
    - Unit

10. Agent Functionality Unit Test
    - ID: AFUT
    - Purpose: Test the agent's basic functionalities.
    - Description: Verify that an agent can get the optimal action for a given state and given its current value function. Verify that the agent can then take a step with that action, and can update the value function given the reward.
    - Inputs: RL agent
    - Outputs: Optimal action for given value function, RL agent with value function correctly modified after action
    - Normal
    - Whitebox
    - Functional
    - Unit

## Test Case Matrix
| Test Case ID | Normal / Abnormal | Blackbox / Whitebox | Functional / Performance | Unit / Integration |
|-|-|-|-|-|
| GLUT | Normal | Whitebox | Functional | Unit |
| CIT | Normal | Whitebox | Functional | Integration |
| CRIT | Normal | Whitebox | Functional | Integration |
| AUT | Normal | Blackbox | Functional | Unit |
| AGIT | Normal | Whitebox | Functional | Integration |
| AGAT | Normal | Blackbox | Functional | Integration |
| ACAT | Normal | Blackbox | Functional | Integration |
| AAIT | Normal | Whitebox | Functional | Integration |
| ACUT | Normal | Whitebox | Functional | Unit |
| AFUT | Normal | Whitebox | Functional | Unit |
