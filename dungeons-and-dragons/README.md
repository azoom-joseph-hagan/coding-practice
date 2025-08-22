# D&D Character Generator

Your friends are ready to play Dungeons & Dragons, but you forgot the dice! Write a program to simulate character creation by rolling virtual dice.

## Your Task

Complete the `DnDCharacter` class in `src/dnd-character.ts` to generate random D&D characters.

### Character Creation Rules

1. **Ability Scores**: Each character has 6 abilities (strength, dexterity, constitution, intelligence, wisdom, charisma)

   - Generate each score by rolling 4 six-sided dice
   - Drop the lowest roll, sum the remaining 3
   - Valid scores range from 3 to 18

2. **Ability Modifiers**: Convert ability scores to modifiers using: `floor((score - 10) / 2)`

   - Ability Score 10-11 range = +0 modifier
   - Ability Score 8-9 range = -1 modifier
   - Ability Score 12-13 range = +1 modifier

3. **Hit Points**: Character's starting health = `10 + constitution modifier`

### Example

Rolling [5, 3, 1, 6] for strength:

- Drop the 1 (lowest)
- Sum: 5 + 3 + 6 = 14 strength
- Modifier: floor((14 - 10) / 2) = +2

## Getting Started

### Prerequisites

- Node.js (version 18 or higher)
- npm or yarn

### Installation

1. Clone or download this project
2. Install dependencies:

```bash
npm install
```

### Running Tests

To run all tests:

```bash
npm test
```

To run tests in watch mode:

```bash
npm run test:watch
```

### Usage

```typescript
import { DnDCharacter } from "./src/dnd-character"

// Create a new random character
const character = new DnDCharacter()

console.log(`Strength: ${character.strength}`)
console.log(`Dexterity: ${character.dexterity}`)
console.log(`Constitution: ${character.constitution}`)
console.log(`Intelligence: ${character.intelligence}`)
console.log(`Wisdom: ${character.wisdom}`)
console.log(`Charisma: ${character.charisma}`)
console.log(`Hit Points: ${character.hitpoints}`)

// Generate a single ability score
const abilityScore = DnDCharacter.generateAbilityScore()
console.log(`Random ability score: ${abilityScore}`)

// Get modifier for a specific ability value
const modifier = DnDCharacter.getModifierFor(15)
console.log(`Modifier for 15: ${modifier}`)
```

### What You Need to Implement

Look at `src/dnd-character.ts` - you'll see a skeleton class with two methods that need implementation:

1. **`generateAbilityScore()`** - Roll 4 dice, drop lowest, return sum of top 3
2. **`getModifierFor(abilityValue)`** - Convert ability score to modifier

You'll also need to:

- Add a constructor that generates all 6 ability scores and calculates hitpoints
- Add properties to store the character's abilities and hitpoints

### Testing Your Solution

```bash
npm test
```

The tests will verify your character generator works correctly. All tests should pass when your implementation is complete.
