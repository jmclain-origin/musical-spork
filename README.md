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

#### Steps

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
