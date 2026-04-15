When planning out your data model, there are a couple points of view you should keep a keen eye on.

> All examples will use a [[Multiuser Dungeon|MUD]] for an example
## Physical
This kind of modeling is the most *developer* minded approach.

How is the data physically stored in the database? How many characters do you expect for each string, how long is each array, and what size are the numbers?

> [!example]
> ```
> Player Char {
> name  = 20 char string;
> level = int;
> dead = bool;
> }
> ```
## Conceptual
This is the way you present it to everyone else.

What data are you storing? What tables/objects are you using to store that data?
## Relative
This is the annoying bit for the database engineer.

How is the data related to each other? What do you index, what do you leave out? How should you join the data together? What identifiers should you use?