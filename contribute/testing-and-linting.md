# Testing and Linting

## Testing Your Code

All tests for the Varphi project are located under the `tests`directory. When testing Python code, please use Pytest as the testing framework (for examples of Pytest tests, please check the existing tests). When implementing a new feature for Varphi, please be sure to test it thoroughly before opening a pull request on GitHub. When you're finished testing your own feature, make sure your new code does not break any existing tests by running all existing tests, as shown below.&#x20;

## Running All Unit and End-to-End Tests

The easiest way to run all tests is to run&#x20;

```shell-session
$ make test
```

This will rebuild Varphi and run all tests.&#x20;

## Linting

For pull requests to be considered, the codebase is checked against a linter. We use [Pylint](https://pylint.readthedocs.io/en/stable/) to do this. The easiest way to run linting on the codebase is to run

```shell-session
$ make lint
```

This will rebuild Varphi and run linting on the `varphi`directory.

## Automatic Testing and Linting

We also have a GitHub workflow to automatically test and lint the code base in the event that a pull request is made to the main branch. You should double check that your code passes these checks when you open a pull request.&#x20;
