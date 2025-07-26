# Submodule Handling

The git [help page](https://git-scm.com/book/en/v2/Git-Tools-Submodules) is surprisingly helpful and readable

## When cloning

So if you clone from Github, it won't copy the files for the submodules

If you've cloned already then do

```
git submodule init
git submodule update
```

If you haven't cloned yet then add `--recurse-submodules` to make it work
```
git clone --recurse-submodules https://github.com/spm1001/spm1001.github.io.git
```

## To update
`git submodule update --remote`

