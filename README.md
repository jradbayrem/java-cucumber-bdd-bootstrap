# kata-bowling-challenge

[![Build Status](https://travis-ci.org/newlight77/kata-bowling.svg?branch=cucumber)](https://travis-ci.org/newlight77/kata-bowling)

## Problem Description

Create a program, which, given a valid sequence of rolls for one line of American Ten-Pin Bowling, produces the total score for the game.

## Rules

We can briefly summarize the scoring for this form of bowling:

- Each game, or “line” of bowling, includes ten turns, or “frames” for the bowler.
- In each frame, the bowler gets up to two tries to knock down all the pins.
- If in two tries, he fails to knock them all down, his score for that frame is the total number of pins knocked down in his two tries.
- If in two tries he knocks them all down, this is called a “spare” and his score for the frame is ten plus the number of pins knocked down on his next throw (in his next turn).
- If on his first try in the frame he knocks down all the pins, this is called a “strike”. His turn is over, and his score for the frame is ten plus the simple total of the pins knocked down in his next two rolls.
- If he gets a spare or strike in the last (tenth) frame, the bowler gets to throw one or two more bonus balls, respectively. These bonus throws are taken as part of the same turn. If the bonus throws knock down all the pins, the process does not repeat: the bonus throws are only used to calculate the score of the final frame.
- The game score is the total of all frame scores.

### Out of scope

Here are some things that the program will not do:

- We will not check for valid rolls.
- We will not check for correct number of rolls and frames.
- We will not provide scores for intermediate frames.

## How to score for Bowling

What makes this game interesting to score is the lookahead in the scoring for strike and spare. At the time we throw a strike or spare, we cannot calculate the frame score: we have to wait one or two frames to find out what the bonus is.

When scoring:

- “X” indicates a strike
- “/” indicates a spare
- “-” indicates a miss

Suggested Test Cases:

- X X X X X X X X X X X X (12 rolls: 12 strikes) = 10 frames * 30 points = 300
- 9- 9- 9- 9- 9- 9- 9- 9- 9- 9- (20 rolls: 10 pairs of 9 and miss) = 10 frames * 9 points = 90
- 5/ 5/ 5/ 5/ 5/ 5/ 5/ 5/ 5/ 5/5 (21 rolls: 10 pairs of 5 and spare, with a final 5) = 10 frames * 15 points = 150


## Implementation with Java and Cucumber

This program is a basic Java Application integrating Cucumber.

### Run it

__Using Maven :__

```
#mvn -N io.takari:maven:wrapper -Dmaven=3.6.2
mvn clean test
mvn clean verify -DCucumberOptions="--glue 'cucumber' --plugin pretty 'features'"
mvn package
java -jar target/kata-bowling-1.0-SNAPSHOT.jar MainApp
```
