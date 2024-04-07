# Git Submodules (Testing Solutions)

This is a test repo for git submodules. Sandbox for testing different solutions for a mono repo architecture other than a package manager workspace configuration.

## Submodules

The project structure consists of a parent module and two child modules. [File tree example](#file-structure)

- [github.com/organization/parent-module-repo](https://github.com/:owner/:repo)
- [github.com/organization/child-module1-repo](https://github.com/:owner/:repo)
- [github.com/organization/child-module2-repo](https://github.com/:owner/:repo)

Note: This repository URL is the root parent. The submodules are hosted in their repository URLs.

---

## Development Workflow

[Git Submodules Docs](https://git-scm.com/book/en/v2/Git-Tools-Submodules)

### Initial Setup

#### Cloning Steps

1. clone the parent repository
2. clone the child repositories

Cloning a repo with submodules will require additional steps.

```bash
# 1st clone the parent repository
git clone https://domain.host/owenr/parent-repo.git
# submodules will be there but empty directories
# next initialize your local configuration
git submodule init
# next update the submodule with latest commit history
git submodule update
```

Alternatively this can be done by simply passing the `--recurse-submodules` flag to the `git clone` command.

 ```bash
 git clone --recurse-submodules https://domain.host/owenr/parent-repo.git
 ```
 
 #### Updates (Fetch/Pull) from Origin

 ```bash
 git submodule update --init --recursive
 # or
 git submodule update --remote --merge
 ```

 #### Commits and Pushes

If we commit in the main project and push it up without pushing the submodule changes up as well, other people who try to check out our changes are going to be in trouble since they will have no way to get the submodule changes that are depended on. Those changes will only exist on our local copy.

In order to make sure this doesn't happen, you can ask Git to check that all your submodules have been pushed properly before pushing the main project. The `git push` command takes the `--recurse-submodules` argument which can be set to either `check` or `on-demand`. The `check` option will make push simply fail if any of the committed submodule changes haven't been pushed.

```bash
git push --recurse-submodules=on-demand
```

### file structure

```stdout
parent-module-repo
  ├── .git
  ├── .gitignore
  ├── .gitmodules
  ├── package-lock.json
  ├── apps
  │   ├── child-module1-repo
  │   │   ├── .git
  │   │   ├── .gitignore
  │   │   ├── package.json
  │   │   ├── package-lock.json
  │   │   └── README.md
  │   └── child-module2-repo
  │       ├── .git
  │       ├── .gitignore
  │       ├── package.json
  │       ├── package-lock.json
  │       └── README.md
  ├── package.json
  ├── package-lock.json
  └── README.md
```
