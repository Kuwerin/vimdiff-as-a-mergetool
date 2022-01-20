# vimdiff as a mergetool


```shell
Auto-merging animals.txt
CONFLICT (content): Merge conflict in animals.txt
Automatic merge failed; fix conflicts and then commit the result.
```

```shell
git mergetool
```

![alt text](https://www.rosipov.com/images/posts/three-way-merge-with-vimdiff.png "vimdiff interface")

From left to right, top to the bottom:

`LOCAL` – this is file from the current branch `BASE` – common ancestor, how file looked before both changes `REMOTE` – file you are merging into your branch MERGED – merge result, this is what gets saved in the repo

Let’s assume that we want to keep the “octodog” change (from `REMOTE`). For that, move to the `MERGED` file (`Ctrl + w, j`), move your cursor to a merge conflict area and then:

```shell
:diffget RE
```

This gets the corresponding change from `REMOTE` and puts it in `MERGED` file. You can also:

```shell
:diffg RE  " get from REMOTE
:diffg BA  " get from BASE
:diffg LO  " get from LOCAL
```

In case you got multiple file conflict you can use `[c` and `]c` to jump to the *previous* and *next* conflict.
Save the file and quit (a fast way to write and quit multiple files is `:wqa`).

Run `git commit` and you are all set!

This instruction is based on [Ruslan Osipov's article](https://www.rosipov.com/blog/use-vimdiff-as-git-mergetool/ "Use vimdiff as git mergetool") helps to understand, how to resolve merge conflicts using vimdiff as a mergetool.
