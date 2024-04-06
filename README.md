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

### Initial Setup

1. clone the parent repository
2. clone the child repositories


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
