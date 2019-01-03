"What do we solve, and how do we solve it?"

## Get a clear understanding of the problem and requirements

* The Goals
  * What are you trying to solve? What is the benefit?
* The Problem
  * Write pseudocode.
  * Manually work through some examples.
* The Data
  * How does the data flow?

You should be able to describe the data in your own terms.

If you make any assumptions about what the problem is, write those down.

* Get clarification from interested parties.

Future-proofing

* Imagine how the problem requirements are likely to change in the future and
  keep those in mind as you implement the solution.

"What do we solve" is about the complete description of the problem.

## Break down the problem

Top Down design: start with a high-level description and break it down.

* **Build a shed**

becomes:

* Build a shed
  * **Build a foundation**
  * **Build a floor**
  * **Build 4 walls**
  * **Build a roof**

becomes:

* Build a shed
  * Build a foundation
    * **Flatten terrain**
    * **Lay down blocks**
  * Build a floor
    * **Build framing**
    * **Add subfloor**
    * **Add floor**
  * Build 4 walls
    * **Build framing**
    * **Install windows**
      * **Frame**
      * **Install sill**
      * **Install glass**
    * **Install door**
      * **Frame**
      * **Install threshold**
      * **Install door**
  * Build a roof

And so on. Keep breaking down tasks until their implementation become obvious.
This might be to the level of `for` loops, if need be.

## Inspiration and Exploration

What does it remind you of?

* Are there similar problems you've solved in the past?

Try small things

* Write "toy" programs to see if they get you close to your goal

Reach out

* Existing code samples
* Documentation
* Google

## Testing

* Keep an eye open for corner and edge cases, especially.

* Does it run quickly enough?
  * Can you make small changes to speed it up?
  * Do you have to revamp the algorithm to get a decrease in time complexity?

## Post-Mortem

When you're done, take a look back at the solution and see what works well and
what doesn't. This helps with future implementations of any problem.
