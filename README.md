# Weapon Game

A C++ console-based game developed using object-oriented programming (OOP), where two players select weapons and battle until one is defeated. This project showcases my skills in C++ and game logic design, with plans to enhance it into a graphical game using the SFML library.

## Features
- **Player Setup**: The console prompts players to enter their names, ages, and genders.
- **Age Restriction**: Players under 15 years old are not allowed to play.
- **Weapon Selection**: Each player chooses from three available weapons (expandable in the future).
- **Gameplay**: Players fight in a turn-based battle until one player is defeated.

## Technologies
- C++
- Object-Oriented Programming (OOP)

## How It Works
1. The game collects player information (name, age, gender).
2. If both players are 15 or older, they proceed to select one of three weapons.
3. The battle begins, and the game continues until one player is defeated.

## Future Plans
I plan to transform this console game into a graphical 2D game using the SFML library, adding visual elements and more weapons.

## Getting Started
1. Clone the repository.
2. Compile and run the C++ file using a C++ compiler (e.g., g++):
   ```bash
   g++ main.cpp -o weapon_game
   ./weapon_game
