# Academic papers

Without sounding too tacky, Lamdu really is a groundbreaking project which includes several novel inventions/discoveries which are worth writing papers about.

This is an area where we are looking for collaborators, as the current Lamdu team doesn't consist of academic researchers.

While we encourage researchers to get in contact with us and collaborate, we understand that people are free to author their own papers and posts describing our discoveries. If you do, we kindly ask to truthfully describe when discoveries originate from Lamdu, and not misrepresent them as your own.

## Papers on features currently implemented in Lamdu

### Friendly static types

Lamdu has a novel interface for type mismatches / "errors":

* Instead of allowing entering invalid code and just reporting an error to the user, when a user enters code that would produce a type-error the mismatching part is automatically wrapped in a "Fragment" (aka "non-empty hole"). Lamdu shows the type of the expression contained in the fragment and its expected type. This way the program always type-checks.
  * Note that this part of our approach already has [academic papers written about it](https://arxiv.org/pdf/1607.04180.pdf) by the [Hazel](http://hazel.org) project. Sadly, their paper [misrepresents Lamdu's approach](https://github.com/hazelgrove/hazelnut-popl17/issues/58) (which they adopted), and does not give proper credit to Lamdu.
* When the type of the expression in the fragment is actually what the user wants its type to be, the user can "insist" on its type via pressing the "space" key on the fragment to "push the type mismatch elsewhere". Then other terms which caused the fragment's expected type to mismatch the term get fragmented instead.
* Lamdu has an interesting approach for API changes and type-mismatches accross definition boundaries. Each global definition invisibly stores the types of its direct dependencies. When a dependency's type changes, the definition's type inference still works with the stored old type. Updating the dependency type is an explicit action with a friendly UI which clearly shows what changed.

### Localization

Lamdu's use of projectional editing enables its support of localization - editing code in several natural languages (currently it only has English and Hebrew but adding more languages is easy).

* Variables are not identified by names, but by hidden unique identifiers. Human readable names are displayed so code looks like normal text-based code.
* The user may select "tags" to name variables. Otherwise Lamdu will auto-generate names for them.
* The tags have names in several natural languages.

#### Prior art / references

(not a complete list)

* MIT's scratch [has localization support](https://en.scratch-wiki.info/wiki/How_to_Translate_Scratch), however there are no user-defined names to be localized and it is not a general-purpose programming language.
* Intentional software [briefly touches on this topic in a video presentation from 2000](https://youtu.be/tSnnfUj1XCQ?t=152). We don't have much more data on their approach (a non-publicly released closed source system) so we don't know how it is implemented.

### "syntax-tree": A novel approach for AST data types

We've created the [syntax-tree](https://github.com/lamdu/syntax-tree) library, which offers a novel approach to represent co-recursive ASTs with co-recursive external fix-points. The library also provides a modular implementation of Hindley-Milner type inference for ASTs defined in this way.

## Future research topics (not currently implemented in Lamdu)

* Structural, static typing aware, revision control
* Designing syntax for better code completions (i.e `x.match` vs `case x of`)
* Topics regarding structural typing (TODO: Eyal please expand on this)
