<p align="center">
  <img src="./assets/galaxy.png" alt="Git-Glitter" />
</p>
<h1 align="center">❯ Glitter</h1>
<h3 align="center">
Next generation <b>Git</b> tooling.
<h3>
<h1></h1>

## ❯ Features
- Config files
- Fast
- Minimal dependencies

## ❯ ✋ What, how and why?

Glitter is a wrapper for Git essentially, allowing you to compress multiple commands into one. Glitter is written in **rust** which not only makes it fast but also efficient. We simply parse your `.glitterrc` and run a few git commands under the hood. Why? Simplicity. If you maintain a project, this is probably the thing for you. You can create a branch and execute commands once the branch is created. You can create templates for commit messages and do multiple things easily.
## ❯ 🎉 Get started

We're so happy to see your interest in Glitter! Leave a ⭐ if you like Glitter!

Firstly, lets create a `.glitterrc` - the configuration file for Glitter.

The glitterrc is basically JSON but a fancy extension. If we want to make it so it automatically templates our commit message we can do it like so:
```json
{
    "commitMessage": "$1($2): $3+"
}
```
and you can use it like so: `glitter push chore deps bump deps`, this would produce the message `chore(deps): bump deps`. As you probably understand, $ is the prefix of arguments, ie, you can do $1 for the first argument, $2 for the second, etc. The + basically means all arguments after the one you specify will be placed there. Lets say we want it to be `chore(Deps): bump deps` and it formats with that case. How? Easy. Lets add another key to our file:
```json
{
    ...
    "commitMessageArguments": {

    }
}
``` 
inside this key we can then add the argument to configure, in this case, the 2nd one, let's add that.
```json
{
    ...
    "commitMessageArguments": {
        2: {

        }
    }
}
``` 
and then, to configure the case, add the key `case` and watch the magic!
```json
{
    ...
    "commitMessageArguments": {
        2: {
            case: "pascal"
        }
    }
}
```
Running `glitter push chore deps bump deps` would then give us the commit message of `chore(Deps): bump deps` 🎉!

## ❯ 📷 FAQ 

> Does **"this hello"** count as 1 or 2 arguments?

**This example counts as 1.** For example `glitter push hello "world how" are you` would give the following arguments:
```
1: hello
2: world how
3: are
4: you
```