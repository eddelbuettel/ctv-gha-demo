# Validate CRAN Task View

This GitHub Action validates proposed changes to a CRAN task view. It is 
designed for use in the [cran-task-views](https://github.com/cran-task-views/)
GitHub organization, but can be run in any other repository as well.

# Using this workflow

Create a file `user/TaskViewName/.github/workflows/validate-ctv.yml`, 
containing:

```yml
on:
  push:
    branches:
      - main
      - master
    paths:
      - '.github/workflows/validate-ctv.yml'
      - '<TaskViewName>.md'
  pull_request:
    branches:
      - main
      - master
    paths:
      - '.github/workflows/validate-ctv.yml'
      - '<TaskViewName>.md'

name: Validate task view

jobs:
  validate-ctv:
    runs-on: ubuntu-latest
    steps:
      - uses: eddelbuettel/ctv-gha-demo/validate-ctv@main
```

Replace `<TaskViewName>` with the name of the task view. Typically, the task view
should be contained in a file named `TaskViewName.md` in the `user/TaskViewName`
GitHub repository.
