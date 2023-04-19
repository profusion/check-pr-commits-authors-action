# check-pr-commits-authors-action
Checks a pull request commits authors according to the email domain. It pass if it's not triggered on a pull request event.

## Inputs
### `EMAIL_PATTERN`
Required email pattern. For example: "^.*@required\\.com$".

### `IGNORED_EMAIL_PATTERN`
Email pattern to be ignored on check.. For example: "^.*@ignored\\.com$".


## Env
### `GITHUB_TOKEN`
Required github token to read the repository pull request.

## Usage example
```yaml
name: Check PR commits authors example

on:
  pull_request:

jobs:
  check-commits-authors:
    env:
      GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
    steps:
      - uses: profusion/check-pr-commits-authors-action@main
        with:
          EMAIL_PATTERN: ${{ vars.EMAIL_PATTERN }}
          IGNORED_EMAIL_PATTERN: ${{ vars.IGNORED_EMAIL_PATTERN }} # this one is not required
```

## Running example
### `Triggered on a no pull request related event`
![Screenshot 2023-04-19 at 13 48 42](https://user-images.githubusercontent.com/61801642/233144933-74611cac-3136-4b4c-a4cd-4c46c686f0de.png)

### `At least one invalid commit author`
![Screenshot 2023-04-19 at 12 38 07](https://user-images.githubusercontent.com/61801642/233127631-defe7572-e0f9-43d6-8af1-a99e2213ea23.png)

### `No invalid commit author`
![Screenshot 2023-04-19 at 12 46 17](https://user-images.githubusercontent.com/61801642/233129773-fb3748b5-ccaf-4756-a671-d1fc07cd3f2f.png)

