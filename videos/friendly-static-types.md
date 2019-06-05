# Friendly Static Types

This video is based on [a presentation given by Eyal in a Tel-Aviv Haskell meetup](https://docs.google.com/presentation/d/e/2PACX-1vR7jyq9qWjbF9nIxysT8U3p_osJYn9tP7-vKvczcVNCy-JPwt7zTrvEZuE-lq2WxJwcg07STAOkpvGq/pub?start=false&loop=false&delayms=3000).

It compares the pros and cons of dynamic typing like in Python to explicit static typing like in Java, then describes how type-inference like in Haskell combines benefits from both while adding new problems (misattributed and complicated type errors), and how Lamdu's approach, named "Friendly Static Typing" provides a novel new interface which combines all the benefits, at the cost of giving up free-form text editing of code.

## Script

(Currently simply adapted from the previous presentation)

### Static types vs dynamic types - the controversey

* Tweet by Gabriele Petronella: ["Static types limit your creativity, but they have flaws too"](https://twitter.com/gabro27/status/1101403050449817600)
* Comic/tweet by Kolja Wilcke: ["static vs dynamic / done!"](https://twitter.com/01k/status/1067788059989684224)
* Pros to static types
  * Catch bugs early
  * Code completions / guidance
  * Refactoring with confidence
  * Performance
* Cons to static types
  * Complicated type errors
    * **Lamdu localizes type errors - allowing execution outside of them** (demo)
  * Program cannot run in the presence of type errors (demonstrated with "favorite things" example)
    * In Lamdu programs can run despite type mismatches as long as they don't reach the errornous branch (demo)
  * Verbosity
    * Not always a bad thing
    * Note that type inference the writers choose the desired level of verbosity
    * Could the readers get to decide? (demo)
    * **Lamdu empowers the reader to control the verbosity**
  * Learning curve

### Problem with type inference - error propagation and blame misattribution

* Neil Mitchell quote: ["As always, the most useful thing in the error message is the line number."](http://neilmitchell.blogspot.com/2008/03/poor-ada-error-message.html)
* Demo: non-empty subsets example in Haskell
* Explain the error
* Can anyone guess where the type error is? Reveal
* Where is the error with verbose types? Reveal
* Demo in Lamdu
* **Lamdu avoids cryptic type errors by containing the error in a sensible and predictable location**

### How is this possible? Projection editing

* Lamdu is not a free-form text editor for code
* All edits preserve valid structure allowing for gapless feedback

#### Why have previous attempts failed? Why is Lamdu different

* WYTIWYS
* Actually reaping the benefits of projectional editing
  * Evaluation demo
  * Lamdu is not a general purpose editor - it has a specific language
* **Lamdu minimizes the costs of projectional editing while reaping new benefits**

### Propagating API changes

* We've demonstrated how blame assignment works inside definitions. How does it work across them?
* Demo
* Lamdu stores types of dependencies
* Mismatching dependencies require an explicit update and are not errors
* After the update, local type mismatches may arise

### Summary table

TODO
