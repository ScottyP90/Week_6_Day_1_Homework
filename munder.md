# Scope Homework: Who Dunnit

### Learning Objectives

- Understand function scope
- Know the difference in between the let and const keywords

## Brief

Using your knowledge about scope and variable declarations in JavaScript, look at the following code snippets and predict what the output or error will be and why. Copy the following episodes into a JavaScript file and add comments under each one detailing the reason for your predicted output.

### MVP

#### Episode 1

```js
const scenario = {
  murderer: 'Miss Scarlet',
  room: 'Library',
  weapon: 'Rope'
};

const declareMurderer = function() {
  return `The murderer is ${scenario.murderer}.`;
}

const verdict = declareMurderer();
console.log(verdict);
```
# it will come back 'The murderer is Miss Scarlet' as the declareMurderer function returns it.

#### Episode 2

```js
const murderer = 'Professor Plum';

const changeMurderer = function() {
  murderer = 'Mrs. Peacock';
}

const declareMurderer = function() {
  return `The murderer is ${murderer}.`;
}

changeMurderer();
const verdict = declareMurderer();
console.log(verdict);
```
# it should come up 'The murderer is Mrs. Peacock' as the changeMurderer function changes the name before the verdict is called.

#### Episode 3

```js
let murderer = 'Professor Plum';

const declareMurderer = function() {
  let murderer = 'Mrs. Peacock';
  return `The murderer is ${murderer}.`;
}

const firstVerdict = declareMurderer();
console.log('First Verdict: ', firstVerdict);

const secondVerdict = `The murderer is ${murderer}.`;
console.log('Second Verdict: ', secondVerdict);
```
# first verdict should be 'The murderer is Mrs. Peacock' and the second 'the murderer is Professor Plum'. the reason is that declareMurderer function only effects the murderer inside. so the murderer Professor Plum is not changed when called for the second verdict.

#### Episode 4

```js
let suspectOne = 'Miss Scarlet';
let suspectTwo = 'Professor Plum';
let suspectThree = 'Mrs. Peacock';

const declareAllSuspects = function() {
  let suspectThree = 'Colonel Mustard';
  return `The suspects are ${suspectOne}, ${suspectTwo}, ${suspectThree}.`;
}

const suspects = declareAllSuspects();
console.log(suspects);
console.log(`Suspect three is ${suspectThree}.`);
```
#suspects should return 'the suspects are Miss Scarlet, Professor Plum, Colonel Mustard' but the second console log should come up saying that 'Suspect three is Mrs. Peacock'. this is because of the lets in the declareAllSuspects function. this mean the name change to suspect 3 only happens inside the function not outside.

#### Episode 5

```js
const scenario = {
  murderer: 'Miss Scarlet',
  room: 'Kitchen',
  weapon: 'Candle Stick'
};

const changeWeapon = function(newWeapon) {
  scenario.weapon = newWeapon;
}

const declareWeapon = function() {
  return `The weapon is the ${scenario.weapon}.`;
}

changeWeapon('Revolver');
const verdict = declareWeapon();
console.log(verdict);
```
#it should return 'The weapon is the Revolver'. the changeWeapon function is set to change the weapon in the scenario. Then when it is called it should change from Candle Stick to Revolver.

#### Episode 6

```js
let murderer = 'Colonel Mustard';

const changeMurderer = function() {
  murderer = 'Mr. Green';

  const plotTwist = function() {
    murderer = 'Mrs. White';
  }

  plotTwist();
}

const declareMurderer = function () {
  return `The murderer is ${murderer}.`;
}

changeMurderer();
const verdict = declareMurderer();
console.log(verdict);
```
#The verdict should be 'The murderer is Mrs. White'. When changeMurderer is called it changes to Mr. Green and then Mrs. White since plotTwist is called in the function.

#### Episode 7

```js
let murderer = 'Professor Plum';

const changeMurderer = function() {
  murderer = 'Mr. Green';

  const plotTwist = function() {
    let murderer = 'Colonel Mustard';

    const unexpectedOutcome = function() {
      murderer = 'Miss Scarlet';
    }

    unexpectedOutcome();
  }

  plotTwist();
}

const declareMurderer = function() {
  return `The murderer is ${murderer}.`;
}

changeMurderer();
const verdict = declareMurderer();
console.log(verdict);
```
#the outcome should be "the murderer is Miss Scarlet". when changeMurderer is called first changes the name to Mr. Green then to Miss Scarlet as unexpectedOutcome is used in the function. the last one plotTwist however does not work as it would only change if function was called in console.log()

#### Episode 8

```js
const scenario = {
  murderer: 'Mrs. Peacock',
  room: 'Conservatory',
  weapon: 'Lead Pipe'
};

const changeScenario = function() {
  scenario.murderer = 'Mrs. Peacock';
  scenario.room = 'Dining Room';

  const plotTwist = function(room) {
    if (scenario.room === room) {
      scenario.murderer = 'Colonel Mustard';
    }

    const unexpectedOutcome = function(murderer) {
      if (scenario.murderer === murderer) {
        scenario.weapon = 'Candle Stick';
      }
    }

    unexpectedOutcome('Colonel Mustard');
  }

  plotTwist('Dining Room');
}

const declareWeapon = function() {
  return `The weapon is ${scenario.weapon}.`
}

changeScenario();
const verdict = declareWeapon();
console.log(verdict);
```
# The murderer weapon should stay the same giving us ' The weapon is Lead Pipe'. when change scenario is run it changes the murderer and room. then unexpectedOutcome function is run but the murderer does not match. then the plotTwist function is run and it changes the room but does not effect the unexpectedOutcome function as it has already been run. so all that has changed is the room not the weapon.

#### Episode 9

```js
let murderer = 'Professor Plum';

if (murderer === 'Professor Plum') {
  let murderer = 'Mrs. Peacock';
}

const declareMurderer = function() {
  return `The murderer is ${murderer}.`;
}

const verdict = declareMurderer();
console.log(verdict);
```
# it should still return 'the murderer is Professor Plum'. while the if does run the let in it means it is contained to the if statement. so Professor Plum remains the murderer.

### Extensions

Make up your own episode!
