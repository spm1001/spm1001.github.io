# Setting up

Useful resources are the [Github Pages setup](https://pages.github.com) and the Quarto [Github Pages guide](https://quarto.org/docs/publishing/github-pages.html)

And for `git` setup, if doing on a new machine:

1. Trying to use `git` should trigger install on MacOS
2. Go and get Git Credential Manager from [here](https://github.com/git-ecosystem/git-credential-manager) - that's a nice, non-Java version that has a MacOS pkg file
3. `git config --global user.name "spm1001"`
4. `git config --global user.email "spm1001@users.noreply.github.com"`

For the blog itself:

1. Make a new repo called `username.github.io` - pick a `.gitignore` template (e.g. the Python one) but don't create a `Readme.md` yet
2. Navigate to an empty directory and run the following:

```
git clone https://github.com/spm1001/spm1001.github.io
cd spm1001.github.io
# Tell Github we don't want Jekyll
touch .nojekyll
# Append ignores for built site so we don't check it in
echo -e "/.quarto/\n/_site/\n" >> .gitignore
cd ..
# Make a default blog
quarto create project blog spm1001.github.io
cd spm1001.github.io
git add .
git commit -m "Commit default Quarto blog"
git push # may trigger GCM
git status # check all is fine
git checkout --orphan gh-pages # switch to gh-pages
git reset --hard # make sure all changes are committed before running this!
git commit --allow-empty -m "Initialising gh-pages branch"
git push origin gh-pages
git checkout main
# Publish once manually
quarto publish gh-pages
```

3. Then create the Github Action per the instructions on the Quarto page. It's just creating a file in `.github/workflows` called `publish.yml` with the following contents. The magic with the curly brackets automatically populates with a secret when a Github machine runs it.

```
on:
  workflow_dispatch:
  push:
    branches: main

name: Quarto Publish

jobs:
  build-deploy:
    runs-on: ubuntu-latest
    permissions:
      contents: write
    steps:
      - name: Check out repository
        uses: actions/checkout@v4

      - name: Set up Quarto
        uses: quarto-dev/quarto-actions/setup@v2

      - name: Render and Publish
        uses: quarto-dev/quarto-actions/publish@v2
        with:
          target: gh-pages
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```



