# Hacktoberfix!

You will never get that T-shirt!

Dear OSS Maintainers,

Tired of closing and commenting on PRs this October after marking them as invalid? Have this simple action do it for you!

See what happens at https://github.com/SanketDG/hacktoberfix/pull/1

Create a `noshirt.yml` in `.github/workflows`:

```yml
name: No T-Shirts for you!

on:
  pull_request:
    types: [ labeled ]

jobs:
  build:
    if: ${{ github.event.label.name == 'invalid' }}
    runs-on: ubuntu-latest

    steps:
    - uses: superbrothers/close-pull-request@v2
      with:
        # You can be more rude if you want to.
        comment: "You will never get that T-Shirt! 👕🚫"
      env:
        GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
    - uses: "jessfraz/branch-cleanup-action@master"
      env:
        NO_BRANCH_DELETED_EXIT_CODE: 0

```
