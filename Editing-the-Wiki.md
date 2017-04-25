We use a pull-request/merge approach for Wiki editing.
This means that we will assume some basic working knowdlege of
[git](https://git-scm.com) and
[GitHub](https://guides.github.com/activities/hello-world/).

## Setup

### Fork the wiki repository
You will need to fork the wiki repository before before you can start editing.
If you don't know what forking means in GitHub lingo, you can read
[this](https://help.github.com/articles/fork-a-repo/) or you can just trust me when I say that a "forked" repository is your
personal copy of someone else's repository stored remotely at GitHub.

- Login with your GitHub account.
- Visit the [cosycat-wiki](https://github.com/emanjavacas/cosycat-wiki) repository.
- Click on the fork button on the upper-right.

### Edit your repository fork
> Before you start editing it is a good idea to "pull" the changes eventually made in the original repository to your local copy, so as to avoid future conflicts when you try to "push" your edits back to the original repository. For this, you need to let git know what is the original repository and then pull.
>```
>    git remote add wiki https://github.com/emanjavacas/cosycat-wiki.git
>    git pull wiki master
>```
Do the changes you wish to be added.
Bear in mind that GitHub wikis use markdown syntax for styling.
Here is a [cheatsheet](https://guides.github.com/features/mastering-markdown/)
for GitHub's own Markdown flavour.
> Tip. If you edit your fork online, you can use GitHub's online editor
> and quickly preview the rendered document you are editing.

### Issue a pull-request to your fork upstream (e.g. main repository)
See [here](https://guides.github.com/activities/hello-world/#pr) for short
instructions on how to open a pull request.
