How to contribute
=================

So, you're a new developer working on ONP?  This document should help you get started.  So you can understand our
branching structure, we use a [successful git branching model](http://nvie.com/posts/a-successful-git-branching-model/) called `git flow`.  Please familiarize yourself 
with it's concepts.

#### Initial Setup

Get the project source code:

 - Create a [github.com](http://github.com) account.
   - Specify your real name on this account, so your collegues will be able to understand who you are.
   - Specify your location (CA, KY, NV, Russia, Germany).
 - Notify your development team lead to get added to the github [opensoft](http://github.com/opensoft) organization.
 - Fork your project's official repository listed at private [opensoft](http://github.com/opensoft) (click the "Fork" button).
 - After the "hardcore forking action" is complete, clone opensoft repository locally.

    `$ git clone git@github.com:opensoft/ONP`

 - Add your fork's repository as a `remote`

    `$ git remote add <username> git@github.com:<username>/ONP`
 
 - Now you should have 2 remotes set up.  `origin` is Opensoft's canonical repository for ONP and should never be pushed directly to.  Push your changes as branches to 
your own `<username>` remote and issue pull requests from there.

Github itself has a fantastic [help section](http://help.github.com/) for new git users that is highly recommended.

#### Staying current

Use the origin remote to ensure your code stays current by syncing your branches with your project's official repository
daily.

    $ git checkout develop
    $ git pull origin develop

__WARNING__: Never commit directly to either the `master` or `develop` branches.  These local branches should always stay in sync with `origin`.  Use named feature or 
bugfix branches for contributing code.

#### Contributing code

Each time you're going to fix a bug on your project, or create a new feature, you'll need to create a new branch.  The branch
should be based off the main development trunk, or release branch closest to the bug or feature that needs work.  Contact
your project lead if you have questions.

Create the branch with the following command:

    $ git checkout -b BRANCH_NAME develop

Use descriptive names for your branches.  Features branches should be named according to the feature itself, while bugfix
branches often are named for the ticket they resolve (`ONP-14721` for example).

 - Make some commits on your branch
 - Include tests to prove the bug is fixed or your feature works
 - Write good commit messages
 - Follow the coding standards for you project
 - Ensure git tracks renames properly

When your work is complete, push your branch to your github fork

    $ git push <username> BRANCH_NAME

Create a pull request by browsing your local fork on github, switching to your `BRANCH_NAME`, and clicking the `Pull Request` button.

#### Pull Requests

A pull request title should detail what's being fixed in which parts of the code.

    [Component] Short title description here.

Please use in the title `[WIP]` prepended to the normal pull request title if the pull request
submission is not yet complete, or if the tests are not yet passing.  

Pull requests should include the following template in the request description:

    Bug fix: [yes|no]
    Feature addition: [yes|no]
    Backwards compatibility break: [yes|no]
    Has tests: [yes|no]
    Project test suite passes: [yes|no]
    Fixes tickets: [comma seperated list of links to tickets fixed by the PR]
    Todo (if incomplete): [list of todos pending]

Below the template, a detailed explaination should be given on the feature or bugfix.

 - What was the cause of the bug?
 - How was the bug resolved?
 - How does the new feature work?

Sometimes, a pull request will require some rework at the request of the project maintainers.  This can be accomplished
by simply pushing more commits to your github fork on the associated branch.

Before resubmitting the pull request, rebase with the base branch and force a push to your origin

    $ git rebase develop
    $ git push -f <username> BRANCH_NAME

