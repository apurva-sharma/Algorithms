BULLS AND COWS:
The program tries to create a program that plays the Bulls and Cows game with a user and tries to minimize the guesses to reach the target.
Code was written on Java 1.6 with eclipse as the IDE.

The program's logging can be controlled by the resources/log4j.properties
Default values are:
log4j.rootLogger=OFF
This will just play the game and output the number of guesses.

In order to better understand what the program does internally, the rootLogger can be set as:
log4j.rootLogger=DEBUG, stdout

Algorithm:
I have implemented 2 strategies:
1. Randomly choosing the next guess in the search space
2. Calculating the next guess based on a heuristic (entropy) as described in http://www.jfwaf.com/Bulls%20and%20Cows.pdf

At each guess, the program prunes the search space by removing all those candidates that do not have the same bulls and cows score
as the guess. This ensures the the correct answer is not eliminated from the search space.
Strategy 2, has a fair amount of computation overhead and slows down the program execution considerably for inital choices
For the original search space size D and pruned search space size N (N<=D), this makes N*D computations.
So, as the paper suggests, I use a mixed strategy where first 3 guesses are made by strategy 1 (which results in a much smaller
pruned search space). From then on, the entropy based strategy takes over which takes a more calculated approach than
trying to guess candidates directly.


