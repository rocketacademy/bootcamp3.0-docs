# Project 1: Video Poker

## Introduction

[Video Poker](https://en.wikipedia.org/wiki/Video\_poker) is single-player Poker where we try to optimise our score by getting the best possible hands. The gameplay is as follows.

1. The user starts with 100 points.
2. When they click the "Deal" button the computer deals a hand of 5 cards. The user can choose any number of their cards to replace with new, random cards.
3. After the user finishes replacing cards, the game assigns points based on the resulting hand. See rankings of Poker hands [here](https://en.wikipedia.org/wiki/List\_of\_poker\_hands#Hand-ranking\_categories).

## Setup

Fork and clone the [Video Poker Repo](https://github.com/rocketacademy/video-poker-bootcamp).

## Base

### Primary Game Logic

1. Create an empty helper function called `calcHandScore` that returns a fixed number of points for now, e.g. 1.
   1. Use [JSDoc function commenting](../course-logistics/tools-syntax-and-glossary.md#jsdoc) with the following attributes.
      1. Description of function
      2. Description of each parameter
      3. Description of return value
   2. `calcHandScore` will take an array of card objects and return the number of points that the user scored for the cards in their hand.
   3. Abstracting `calcHandScore` allows us to construct the primary game logic without worrying about hand-scoring logic.
      1. It will also make testing hand-scoring logic easier because we can test scoring of individual hands without running the whole game.
2. Code the primary game logic using `calcHandScore` wherever we wish to calculate the score of a given hand. This logic should include the following.
   1. The user has a global number of points.
   2. The user clicks a button to deal cards.
   3. The user selects which cards they want to keep.
   4. The game replaces the unselected cards, calculates the hand score, and updates total points.
3. Lay out game controls for mobile (portrait orientation), and set the `max-width` CSS property of the container so the layout is still friendly on a wider screen.

### `calcHandScore`

1. After we have a playable version of the game, add logic to `calcHandScore`.
   1. Add logic for detecting each hand (e.g. full-house, flush, 2 pair) 1 at a time.
   2. Test the logic for each hand before moving onto the next hand.
   3. Consider using a JS Object to track frequencies of specific ranks or suits. This might make it easier to detect hands such as flushes, full houses, and X-of-a-kind. See [0.4: JS Object as Tally](../0-language-and-tooling/0.4-js-object-as-tally.md) for an example.
2. Hard-code the arrays of card objects we will need to test our logic.
   1. Put these test hands in a separate file, e.g. `testHands.js`.
3. Don't forget to test the negative cases, e.g. do we still win/lose the right number of points if we don't get the hand we are currently testing?

#### Example Usage of `calcHandScore`

```javascript
const playerHand = [
  { rank: 2, suit: 'hearts', name: '2' },
  { rank: 2, suit: 'diamonds', name: '2' },
  { rank: 5, suit: 'spades', name: '5' },
  { rank: 7, suit: 'spades', name: '7' },
  { rank: 9, suit: 'hearts', name: '9' },
];

// calcHandScore returns the number of points a given hand earns.
const pointsForHand = calcHandScore(playerHand);
```

## Comfortable

### Polish

"Polish" your app so that it is presentable to the public. This can involve the following attributes.

1. Does the app run without errors or unexpected behaviours?
2. Are variable names concise and precise?
3. Do we have [JSDoc comments](https://jsdoc.app/about-getting-started.html#adding-documentation-comments-to-your-code) above functions and inline comments above code that could be confusing to others?
4. Is each function sufficiently small and modular?
5. Is the visual design clean?
   1. Muted colours
   2. Elements have padding
6. Is the page responsive? Does it look good on both mobile and desktop?
7. Do we want to incorporate sounds?
8. Do we want to incorporate animations?
   1. We can google for CSS animations and append GIFs to get motion
9. Do we want to incorporate 3rd-party art? The following are useful resources.
   1. [https://conceptartempire.com/free-game-art-sites/](https://conceptartempire.com/free-game-art-sites/)
   2. [https://itch.io/game-assets/free](https://itch.io/game-assets/free)
   3. [https://opengameart.org/](https://opengameart.org)
   4. [https://www.gameart2d.com/freebies.html](https://www.gameart2d.com/freebies.html)

## More Comfortable

The goal of this project is to practise frontend. Please reach a good level of polish before attempting the following More Comfortable features.

### Probabilities

Show the user the probability of getting each winning hand if they choose to switch the cards that are currently selected.

### 7 Card Stud

Implement 7 Card Stud rules for Poker instead of 5 Card Draw.

## Project Submission and Past Student Projects

Once done with your project, please submit it by adding it to the [Rocket Bootcamp Projects spreadsheet](https://docs.google.com/spreadsheets/d/1YZ39naj5E6mNNkQ1akR\_FgeFO\_kM6aWCAr8zqrFOkt4/edit?usp=sharing) in your batch-specific sheet. Feel free to view past student projects in previous batches' sheets.

## Disclaimer

{% hint style="danger" %}
**Rocket Academy does not endorse gambling.** We chose Video Poker as a project because of its complex rules that help facilitate coding instruction.
{% endhint %}
