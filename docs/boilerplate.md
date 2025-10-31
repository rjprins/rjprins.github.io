# On boilerplate code

Boilerplate code might seem harmless, but it can subtly bload a codebase and make it seem a lot larger and more complicated than it really is.
What do I mean with boilerplate code?
<look up definition>

Maybe I'm also talking about a related concept, which is "organizational code".
All code related to not actually the business logic, but organizing the business logic.
For example, if you split code into two files, then imports from one file to the other are organization code. A function definition and function call are also organizational code.
Clearly, some organization code is necessary. And functions are a great idea. However it is important to remember there are downsides to functions.
First of all, they are an indirection. Wherever your see a function call, you have to make the decision "Am I going to lookup the function definition and read it?". This complicates reading.
Functions with very good names and clear goals will allow you to skip over them, which is a gain in readability if it hides details you know you don't care about.
At other times, functions (and other objects) are used to semantically organize code. Model-View-Controller would be an example of that. Model classes go into models, view functions in views, and the glue to make it all work goes into controller.
This is nice if you are new to a code base and are just looking at the file structure.
But as soon as you start reading you find yourself switching from file to file.
Very often in applications functions in the controllers are only called from one place: The view functions. So the functions are not there for reusability, but rather for code organization.
Generally what I see is that the organization is per code pattern.
So view functions all follow a pattern described by a web framework. And the controller functions all follow some application specific or no pattern.

