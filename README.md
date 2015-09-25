INTRODUCTION
------------

This is a small script to visualize the time when commits are committed in a set
of git repositories. The idea is stolen from Github's punchcard picture (Kudos to
Github)!

If you want to visualize a single git repository instead, you should have a look
at
[the original punchcard program](https://github.com/guanqun/git-punchcard-plot)
instead.

SCREENSHOT
----------

Here's the generated picture from MongoDB project:


![MongoDB Punchcard](mongodb-output.png)

WHY IS IT INTERESTING
---------------------

It shows how a set of repositories are developed in developer's time. If you
work on multiple projects, whether it is for work or in your spare time, you can
determine when you're working.

As I see it, I can get a simple clue whether a project is a spare time project
or this project is totally under a company's control, thus resulting in commits
from 8AM to 6PM, Monday to Friday.

PREREQUISITE
------------

- python (of course!)
- pycairo module
- git

Then you're free to go!

USAGE
-----

- `cp git-multipunchcard /usr/local/bin` (or somewhere else on your `$PATH`)
- make sure that `/usr/local/bin` is in your `$PATH` environment variable.
- invoke `git multipunchcard`

If you want a different name, then simply invoke `git multipunchcard file=<another-name.png>`.
The default width of a picture is 1100px.  If you'd like
to have a higher resolution, you can run `git multipunchcard file=<another-name.png> width=<new-width>`.

If you would like to filter by a particular author then do so as follows. (all parameters are available)
`git multipunchcard -- --author=<authorname>`

The image gets scaled automatically.

The easiest way to work on a set of projects is to make a new directory, then
clone all the projects to that directory. What I tend to do is something like
this:

```shell
mkdir -p aggregate-data
cd aggregate-data
for project in a b c; do git clone "git@github.com:orgname/$project"; done
git multipunchcard file=jean.png -- --all --since='1 year ago' --author=jeannikl
```

This will collect all the commits I've authored in all branches the last year
and make a punchcard for them.

LICENSE
-------

This project is under public domain, you can do whatever you want ;)
However, if you're improving this tool a bit, you can freely fork it and then
send me back a pull request. I would be very glad to integrate it.
