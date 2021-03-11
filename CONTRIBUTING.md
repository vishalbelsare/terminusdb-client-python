# Contributing to TerminusDB Client

Thanks for interested to contribute to TerminusDB Client, to get started, fork this repo and follow the [instruction setting up dev environment](#setting-up-dev-environment). If you don't have idea where to start, you can look for [`good first issue`](https://github.com/terminusdb/terminusdb-client/contribute) or `help wanted` label at issues. All pull request should follow the [Pull Request Format Guideline](#pull-request-format-guideline) and pull request (PR) that involving coding should come with [tests](#writing-tests-and-testing) and [documentations](#writing-documentation). **All pull request should be made towards `dev` branch**

## Setting up dev environment 💻

Make sure you have Python>=3.6 installed. We use [pipenv](https://pipenv-fork.readthedocs.io/en/latest/) for dev environment, to install pipenv:

`pip3 install pipenv --upgrade`

[Fork and clone](https://help.github.com/en/github/getting-started-with-github/fork-a-repo) this repo, then in your local repo:

`pipenv install --dev`

To “editable” install the local Terminus Client Python:

`pip3 install -e .`

**to be able to run integration tests, local installation of docker is required**

We use [shed](https://pypi.org/project/shed/) to lint our code. Although you can do it manually by running `shed`, we highly recommend setting up the pre-commit hook to do the linting automatically.

To install the pre-commit hook:

`pre-commit install`

## Writing tests and testing ✅

We are using [pytest](https://docs.pytest.org/en/latest/) for testing. All tests are stored in `/tests`

We also use tox to run tests in a virtual enviroment, we recommend running `tox` for the frist time before you make any changes. This is to initialized the tox enviroments (or do it seperately by `tox -e deps`) and make sure all tests pass initially.

To run the unittests without integration tests:

`pytest terminusdb_client/tests/ --ignore=terminusdb_client/tests/integration_tests/`

To run all tests including integration tests:

`tox -e test`

To run all checks and auto formating:

`tox -e check`

To run all tests and checks:

`tox`

**please make sure `tox` passes before making PR**

## Writing Documentation 📖

Please follow [numpydoc docstring guide](https://numpydoc.readthedocs.io/en/latest/format.html) for documentation. It is important to follow the formatting as all documentation will be automatically rendered using [Sphinx](https://www.sphinx-doc.org/).

To render the documentation locally (for preview before making your PR):

```
cd docs
make html
```

The built documentation will be in `/build/html/` which you can open `index.html` in your browser to check.

*now you are in docs directry, make sure you go back to the top directry of the repo if you want to commit and push*

## Pull Request Format Guideline 🏁

Please put the type of the pull request in the title:

* [Doc] for documentation
* [Bug] for bug fixes
* [Feature] for new features
* [WIP] for work in progress (will not be reviewed)

Also, if there is a related issues, please also put the issue numbers in blankets in the title, for example: (#10)

It will be great to describe what you have done in the pull request (more detail the better). If there is a issue that can be closed by this PR, you can put `Close #XX` or `Fix #XX` (while XX is the issue number) to close that issue automatically when your PR is merged.

Following the guideline makes the reviewing process of the PR much efficient.