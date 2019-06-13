# Friendly Static Types

This video is based on [a presentation given by Eyal in a Tel-Aviv Haskell meetup](https://docs.google.com/presentation/d/e/2PACX-1vR7jyq9qWjbF9nIxysT8U3p_osJYn9tP7-vKvczcVNCy-JPwt7zTrvEZuE-lq2WxJwcg07STAOkpvGq/pub?start=false&loop=false&delayms=3000).

It compares the pros and cons of dynamic typing like in Python to explicit static typing like in Java, then describes how type-inference like in Haskell combines benefits from both while adding new problems (misattributed and complicated type errors), and how Lamdu's approach, named "Friendly Static Typing" provides a novel new interface which combines all the benefits, at the cost of giving up free-form text editing of code.

## Current draft

For current rough draft with low quality audio and unpolished visuals [see here](https://www.dropbox.com/s/febl1sxfnaj6tzy/Static%20Types%20Work%20in%20Progress.mp4?dl=0).

## TODOs

* High quality audio

## Script (for recording)

Hi! I'm Yair and I want to show you a novel user interface for static types.

We'll start by just showing it with a simple code example.

This is Lamdu. Lamdu is a programming environment.
It currently shows an if expression with three holes.
Holes are place-holders for missing code in incomplete programs.

Underneath the holes we see type annotations.
The condition needs to be a boolean,
and the two branches should have the same type, denoted by the matching type variable "a".

Now let's see what happens if we type a string into the top branch.
Lamdu now shows that the second hole should also have the type "Text".

What would happen if we would type a number into it?
This generates a type mismatch: Its type is "Num" but it's expected to be "Text".
The red rectangle represents this mismatch and is called a "fragment".

But what if we really want a number there?
Lamdu lets us "insist" on this type with the close-bracket keyboard shortcut.
This refragmented the code and placed the type mismatch on the other branch.

Unlike other programming languages with type inference,
which arbitrarily assign blame for type errors.
Lamdu by default predictably assigns the errors to the newest code edits.
As this isn't always the desired result,
Lamdu empowers the user to reassign the blame to conflicting code.

Before we expand on this more,
let's take a step back and review common approaches to types in popular programming languages.

We'll start by comparing dynamic programming languages like Python and JavaScript,
to explicitly typed languages like Java and C#.
 
* Static languages catch type errors in compile time, never in production,
  and the programs are also faster and more efficient
* They offer type-directed completions
* But they are quite verbose.
* And you can't do anything with the program until you fix the type errors
* When type errors occur, dynamic languages provide concrete examples for values -
  making errors easier to decipher
* While static languages like C++ and Haskell are infamous for their cryptic type errors

But what about statically types languages with type inference, like for example Haskell?
These don't suffer from the verbosity of explicit static languages,
but we pay for that in the propagation and misattribution of blame in type errors.

How are these issues addressed in what we call "Steady Typing"?
* We enjoy the normal performance and static checking benefits of static types.
* Type information and completions are available at all times. Let us demonstrate

Here's another piece of code in Lamdu.
It contains two holes, and Lamdu always shows type annotations for holes.
Now let's go to the boolean hole and type in "x".
We got a fragment because "x" is a number and we need a boolean.
Note that unlike other static languages, the type mismatch is localized with a fragment.
So everything is still validly typed!
So we still see the expected types for holes.
If we want we can also see the types of everything.
This is quite verbose so usually we won't want to see the times as we code.
And because this is Lamdu, we can also see the values!

So types are steadily available even when the program is incomplete and has type mismatches.
As a result type assisted editing is always available.
And as we've also shown, the reader controls the verbosity of type information.

Next - can we run code despite of type errors? Let's see!

This is a simple function enumerating favorite things.
Despite containing a type mismatch, we can still run code including this function!
Only when evaluates reaches the mismatch, it cannot work.
So we can run despite of errors!

And as we've demonstrated in the beginning of the video,
type mismatches have a friendly user experience.
Type mismatches are localized in fragments
so there are no errors, and type-based facilities are always available.
Blame is predictably assigned,
and the user has full control and can reassign it easily.

Now, let's discuss another important topic in the debate between dynamic and static types.
This one is related to code maintenance and refactoring.
When we change the type of a function, how do we maintain this change across the code base?

In dynamic languages - we better have a comprehensive test suite!
That will cover every usage of the function.

With static types, the compiler helps guide us to all the call that need to be updated.
But when several functions change like when updating a library,
the free propagation of type information with type inference can make things complicated.

Can we help the user handle the API changes? Let's see.

Here we see a code example.
At the top the "sum of digits" function is called with the argument 12345,
and the result for that is 15.
Below it we see the definition of "sum of digits".
It uses the "digits" function and calls the "sum" function on the result of that.
Let's turn off the value annotations!
They are invaluable when debugging, but they also clutter the code.
This is nicer to look at!
Now let's modify the "digits" function so that it works for any given base, not just base 10.

As we've added the "base" parameter, a few things happened.
One cosmetic thing that happened,
is that Lamdu's auto-layout split the line so that the code fits within the width of the window.
Also, as we've added the parameter, the recursive call to "digits" got the new parameter added to its call.

After making this change, what would happen if we were to execute the code?
It cannot run!
This is because its evaluation calls a dependency which has changed.

What does Lamdu show us here?
When the "sum of digits" function originally called the "digits" function its argument was just a number.
Now it gets a number and a base.
Note that before updating its type,
its previous type is used for type inference in the "sum of digits" function,
allowing everything to still be validly typed.
This allows us to update the types of our dependencies one step at a time.

Note that in order to do this,
Lamdu invisibily stores the types of all dependencies for every definition,
unlike other programming languages that only store what you see.

How can Lamdu provide all these benefits?
Why didn't the other languages choose this approach as well?
A key difference is that these other programming languages are based on plain text files,
and perhaps you've noticed already, but Lamdu is not.
Lamdu is a projectional code editor.
We acknowledge that past attempts at creating projectional editors have not caught on,
but unlike past attempts we focus on also retaining the benefits of text editing,
foremost the what-you-type-is-what-you-see principle.
For more information on that, see our previous video.
Bye for now!
