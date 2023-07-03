# Simple Git workflow 

As our team has integrated git into our software development project, its important to notice the importance of git flow to speed up and better trace the progress of your project

## Git Flow

We recommend to use [Gitflow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow). 

**WE ARE HIGHLY RECOMMEND EVERYONE READING THIS DOC BEFORE YOU START ANY REPOSITORY. THIS WILL MAKE YOUR WORK MUCH TIDIER AND TRACABLE FOR ANY PEOPLE THAT YOU WORK WITH** 

Simply say
Any features to the repository should be started as branches coming off the **Development** branch and be prefixed with `feature/` (or an appropriate semantic prefix for commits that don't technically constitute a true 'feature', e.g. 'refactor/[refactor-description]' etc...). Any patches for production should be applied directly to **Master** AND **Development** and be prefixed with `hotfix/`. All branches should be associated with a pull request for merging back into **Development** or **Master** branches. For non-trivial commits (or in general), having someone else approve your pull request is preferred.

### Workflow for new feature branch
- Start on Development branch (`git checkout development`)
- Pull recent changes (`git pull`)
- Create new branch (`git checkout -b feature/[feature-name]`)
- Add changes (`git status` to see changes, `git add .` to add all changes)
- Commit changes (`git commit -m 'commit message'`)
- [Rebase if necessary: see note below]
- Push to Github (`git push origin feature/[feature-name]`)

Once the local feature branch is pushed up to Github, initate a pull request to have it included into the main **Development** branch. As a general rule, you should not accept your own pull request.

#### Rebasing in a feature branch

Should other contributors commit changes to `development` while a feature branch is under development, a **Rebase** is required for a clean project merge. For a description of rebasing please see the [docs](https://git-scm.com/docs/git-rebase). For a description of rebasing vs. plain old merging see this [blog post](https://medium.com/@justintulk/git-rebase-vs-git-merge-for-beginners-aecc1ef1c718#.g89chz4h2). In short, _rebasing_ ensures that your changes are applied on top of changes merged into `development` by other feature branches completed since the feature branch in question was split off. It isolates conflict resolution to the feature branches and keeps merge conflict resolution commits from polluting the primary `development` branch history.

To do a rebase, after your last commit into `feature/[feature-description]` please follow the following process:

- checkout development `git checkout development`
- refresh development branch to latest `git pull`
- re-checkout feature branch `git checkout feature/[feature-description]`
- apply rebase `git rebase development` **NOTE** - rebase must happen from WITHIN your feature branch
- resolve any merge conflicts appropriately 
- push rebased feature branch to remote (see above)

### Workflow for hotfix applied directly to **Master**
- Start on Master branch (`git checkout master`)
- Force pull Master (`git pull -f`)
- Create new hotfix branch (`git checkout -b hotfix/[hotfix-name]`)
- Add changes (`git status` to see changes, `git add .` to add all changes)
- Commit changes (`git commit -m 'commit message'`)
- Push to Github (`git push origin hotfix/[hotfix-name]`)

Once the local hotfix branch is pushed up to Github, initate a pull request to have it included into the main **Master** branch. As a general rule, you should not accept your own pull request. Once approved, merge **hotfix/[hotfix-name]** into **Development** as well as **Master**.

## For more info

#### [git cheatsheet](https://github.com/PolyU-Robocon/PolyU_Robotics_Basic_Tutorials/blob/master/git_cheat_sheet.pdf)

#### [basic git tutorial](https://github.com/PolyU-Robocon/PolyU_Robotics_Basic_Tutorials/tree/master/Git)