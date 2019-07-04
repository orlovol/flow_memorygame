# Memory Game

This is an implementation of Memory Game in [Flow programming language](https://flow9.org/).

Flow allows compiling into single HTML/Javascript page, so this may be a good place to see how it can be done.

[Live version](https://orlovol.github.io/flow_memorygame/index.html) of the game.


## Setup

I've included a [simple install guide](INSTALL.md) that should get you up and running.
It focuses on minimal working setup for compiling Flow code using JavaScript target.
Its Linux-only, but the steps are roughly the same for other OSes.

## Contents

This project is written as an example of Flow capabilites and as a simple tutorial to learn the language.
It's split into 12 easy to follow steps, and each commit contains small text description to help figure out what is happening.
Links for commits are below, along with texts for basic idea of what's inside.
For more information about used functions check the [Flow sources and documentation](https://github.com/area9innovation/flow9).

1. [Initial commit](https://github.com/orlovol/flow_memorygame/commit/18ccf4f)
    ```
    Let's start by adding sandbox/hello.flow to check if we can run it.
    Add build script that creates html bundle with our app, and basic gitignore.
    ```

2. [Use Tropic](https://github.com/orlovol/flow_memorygame/commit/6a497b9)
    ```
    Next step is to import Tropic UI library, that will provide us with everything needed to create visuals.
    Let's replace Text with TText, and add FontSize style to make it bigger.
    By default forms are drawn in top-left, so we can use TCenterX to align text horizontally.
    "|>" is a pipe syntax that wraps left side argument with right side single-parameter function.
    ```

3. [Draw Rectangles](https://github.com/orlovol/flow_memorygame/commit/0e8e466)
    ```
    Now let's add a function that would return a simple square card.
    TCols & TLines allow us to group forms side by side.
    ```

4. [Add interactivity](https://github.com/orlovol/flow_memorygame/commit/87a47dc)
    ```
    Rectangles are good, but we need to handle card clicks.
    To separate model from view, we add Card structure with basic fields - color and some boolean flag behaviours.
    At any point we can check behaviour value and draw either face or back of the card.
    Clicking the card would toggle the opened value.
    ```

5. [Grid](https://github.com/orlovol/flow_memorygame/commit/6c93754)
    ```
    Now that we can create colored cards, we can do as many colors as we like.
    We multiply color choices and create a pretty grid.
    ```

6. [Fusion](https://github.com/orlovol/flow_memorygame/commit/e7e4577)
    ```
    First, we separate Card creation and drawing.
    Then, we make openedStates Transform object that emits signal with updated values when any card changes opened state.
    After that, we make openedCount object that emits the number of opened cards only.
    Our game logic is to close cards when we already opened enough to form a match pair.
    We can achieve this by drawing invisible overlay that will handle click to close cards.
    To actually subscribe on these signals and call required function, we wrap our game form into TConstruct.
    It manages our subscriptions while the form is shown, unsubscribing when the form is destroyed.
    * Never forget to unsubscribe when you're done *
    ```

7. [Game, set, match](https://github.com/orlovol/flow_memorygame/commit/9e8bc67)
    ```
    Flipping cards is nice, but we can't achieve victory by doing just that.
    It's time to set cards of the same color as solved.
    Moreover, we need to ignore them when closing cards.
    ```

8. [Graphics](https://github.com/orlovol/flow_memorygame/commit/0b05ec3)
    ```
    Colored cards are good, but images are even better.
    Adding them is as simple as passing filename to the TPicture tropic.
    However, for maximum customization we ought to use TRawButton.
    It allows setting different forms for button states,
    but we will supercharge single tropic to handle all those states.
    ```

9. [Congratulations](https://github.com/orlovol/flow_memorygame/commit/1f62aad)
    ```
    It always feels good to be praised for hard work.
    Let's add a popup dialog that does exactly that, only thing we need is the number of solved cards.
    ```

10. [The only winning move](https://github.com/orlovol/flow_memorygame/commit/f391d80)
    ```
    It's always a good idea to track progress.
    Simple counter of moves will keep us sane.
    ```

11. [Rinse and repeat](https://github.com/orlovol/flow_memorygame/commit/b919e04)
    ```
    As Bruce Lee said:
        " I fear not the man who has practiced 10,000 kicks once,
        but I fear the man who has practiced one kick 10,000 times. "

    To add replayability we need to signal that game is over and restart everything.
    For that we need another function that will redraw the game scene in mutable Tropic.
    ```

12. [Finish](https://github.com/orlovol/flow_memorygame/commit/d7794a2)
    ```
    And we're done!

    All that's left to do is fix scaling and layout a bit, for better mobile experience.
    * Note that layout is not dynamic, so you need to reload page if you use devtools mobile preview *
    And for better development experience we can export our game function,
    so anyone can now import & embed it in their serious business programs.

    Hope you've had fun & good luck with your own creations!
    ```

### More improvements

These are community-driven improvements, that were added after the main tutorial was written.
They bring much more to the table, and deserve a special list.

13. [Auto-close cards](https://github.com/orlovol/flow_memorygame/commit/e13aab2) by [danichmur](https://github.com/danichmur)