## Transcript

We code in many different languages,
but ironically, we all code in the same language: English.

The function names and the language keywords, are all in English

But not everyone knows English.
In fact, most of the world doesn't.
Do we have to exclude them from programming?

This is Lamdu.

Lamdu is a programming language where the code is stored as a data structure.
One of the benefits that this approach enables is that code is isn't in any specific natural language.
The user can choose to view the code in any natural language that they like,
it's just a display preference.

This is how it works:
Even though Lamdu has a text-like UI the code is stored as a data structure.
When referring to the function sum, a textual language would actually store the text "sum" in the code.
In Lamdu, it's referred internally by a unique identifier.
The identifier corresponds to the function definition,
which also doesn't store the name "sum", but instead points to a name object.
The name object stores the name in several languages.

Let's see how it looks like in Lamdu.
If we press "enter" on the use of "sum", it opens up the "sum" function.
The "enter" key on its name in its definition opens the name object.

Lamdu currently supports English, Italian and Hebrew.

Let's give this function a new name: "total".

The "create new" option indicates that there is no existing name object called "total".
Note that when we selected the new name it also appears in the call site of the function originally called "sum".
Unlike textual programming languages, in Lamdu renaming the function is a single change in the data structure.

I'd like to give a mention to some related works.
There are actually quite a few non-english programming languages,
each still targetting a specific natural language.
And there are also block languages like MIT's Scratch,
which have supported localization for a while.
But these do not support user-defined function names.

The only project we're aware of, that looks similar to Lamdu, was Intentional Software's.
This is their demo from more than 20 years ago:

"Or if the project is international,
we could have a translated name in the national alphabet displayed in Unicode"

But from what we've heard, that project has been discontinued and never publicly released.
Lamdu on the other hand, is an open-source project, and everything we've demonstrated is already available.
But it's not ready for production just yet.
Creating a non-textual programming language and a whole development environment is no small feat.
Since starting almost 10 years ago, we've implemented a significant part of it.
But there's still more work ahead before it can be useful for production.

Localization is just a small part of Lamdu.
We've previously made presentations about "Steady Typing" and its Live Programming aspects,
which you can watch if you want to learn more (NOTE: need to flash links in the video at this point).

Our goal is to make a useful programming language that is delightful to use.
Lamdu is currently coded in Haskell, and the long term plan is to make it self-hosted.

If you share our vision for programming, we would really love your help and welcome contributions of all kinds.

If you'd like to see Lamdu localized to your language, it's pretty easy to add a new language.
We would really appreciate that contribution too.

We'd like to thank Giovanni Ziulianni for contributing the Italian translation. Thanks, Giovanni!

Thanks for watching!
