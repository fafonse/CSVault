Ooopsey, you just fucked up your code!!!! Now your local repository and the remote both out of sync and you can't merge without having to tussle with it a bit.

## Fixing the shit
First you have to pull from your remote. That way you aren't fucking around on the cloud but on your own computer.
But first, you got to choose whether or not you want to *rebase*.
### Rebase
Rebasing essentially changes the source history to be "cleaner".
When you rebase, you hide the divergence/conflicts. This can be nice for log readability, but can make it harder to follow the source history.
If you decide to not rebase, you instead keep the divergence in the source history, showing your work publicly. *This is the preferred method for Jeff's class.*

```
A═╦═══>B═╗                
  ╚═╗    ╠═>D VS.  A═>B═>C
    ╚═>C═╝                

No rebase          Rebased
```

When actually using git in the terminal, 
- ``git pull --no-rebase`` 
- ``git pull --rebase``

### Managing Conflicts
Once you pull your remote into you local repository, you have to manually sort out all the conflicts. 
Git doesn't change any of your filenames, but inside you'll find that there's a bit of new text. 
That new text just is padding showing what's from the remote and what's from your local repo.
This is the hard part, where you just manually make sure you can marry the two copies together.