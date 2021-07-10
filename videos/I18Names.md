## Transcript

We code in many different languages,
but ironically, we all code in the same language: English.

The function names and the language keywords, are all in English

But not everyone knows English.
In fact, most of the world doesn't.
Do we have to exclude them from programming?

This is Lamdu.
Lamdu is a programming language where the code is stored as a data structure.
One of the benefits of that this approach enables is that code is isn't in any specific natural language.
The user can choose to view the code in any natural language that they like,
it's just a display preference.

This is how it works:
Even though Lamdu has a text-like UI the code is stored as a data structure.
When referring to the function sum, a textual language would actually store the text "sum" in the code.
In Lamdu, it's referred internally by a unique identifier.
The identifier corresponds to the function definition,
which also doesn't store the name "sum", but instead points to a name object.
The name object stores the name in several languages.

Let's see how it looks like Lamdu.
If we press "enter" on the call to "sum", it opens up the "sum" function.
The "enter" key on its name in its definition would open the name object.
By the way, we currently support English, Italian and Hebrew.
To further illustrate the mechanism,
let's rename this function to have a different name: "total".
The "create new" option means that there is no existing name object called "total".
Note that when we selected the new name it also appears in the call site of the function originally called "sum".
Unlike textual programming languages, in Lamdu renaming the function is a single change in the data structure.

I'd like to give a mention to some related works.
There are actually quite a few non-english programming languages,
each still targetting a specific natural language though.
And there are also block languages like MIT's Scratch,
which have supported localization for a while.
But it doesn't have user-given function names.

The only project we're aware of, which looks similar to what we do, was Intentional Software's.
This is their demo from more than 20 years ago:

"Or if the project is international,
we could have a translated name in the national alphabet displayed in Unicode"

But from what we've heard, that project has been discontinued and never publicly released.
Lamdu on the other hand, is an open-source project, and everything we've demonstrated is already available.
But it's not ready for production just yet.
Creating a non-textual programming language with its development environment in unison is no small feat,
and since starting almost 10 years ago, we did code a significant part of it.
But there's still more work ahead before it can be useful for production.

Localization is just a small part of Lamdu.
We've previously made presentations about Steady Typing and its Live Programming aspects,
which you can watch if you want to learn more.
Our goal is to make a useful programming language that is delightful to use.
Lamdu is currently coded in Haskell, and the long term plan is to make it self-hosted.
If you share our goal, we would really love help.
I'd like to thank Giovanni Ziulianni for contributing the Italian translation.
If you'd like to see your language supported as well, it's pretty easy to add a language if you know it. We would really love that contribution too.

Thanks for watching!
