Any subclass should be able to do the same shit it's superclass does.

> [!example]
> Given a character class in a game, the subclasses `monster` and `player` should both be able to do anything a `character` can do. I.E doing `player.setPos()` should not crash compared to `character.setPos()`