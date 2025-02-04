# Add Reviewers

## Overview

This repository demonstrates using `CODEOWNERS` to assign reviewers to PRs that modify code.

CODEOWNERS works on:

- public repositories with GitHub Free
- public and private repositories with paid GitHub accounts.

## Usage

Add a `.github/CODEOWNERS` file.

- Each line should have a file pattern and one or more owners.
- Owner is important, last matching owners are applied.

```yml
*     @developer1 # This is the default owner for all files.
*.css @designer1  # Now, "designer1" is owns all CSS files.
```

- Email addresses may be used instead if user IDs.

```yml
*.js frontent@example.com
```

- Team, in the format `@org/team-name` may be used.
- The `docs/` pattern will match all files and folders in `docs`.
- The `docs/*` pattern will match files in `docs` but NOT sub-folders.
- Multiple reviewers may be declared, at least ONE is required for approval (but not all)

```yml
# In this example, any change inside the `/scripts` directory
# will require approval from @doctocat or @octocat.
/scripts/ @doctocat @octocat
```

@see [About code owners](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-code-owners)

## Branch Protection

- Edit branch protection rules and enable "Require review from Code Owners".
- To protect a repository fully against unauthorized changes:

```yml
/.github/ @owner_username
```

@see [CODEOWNERS and branch protection](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-code-owners#codeowners-and-branch-protection)

## Gotchas

- Escaping a pattern starting with `#` using `\` so it is treated as a pattern and not a comment doesn't work
- Using `!` to negate a pattern doesn't work
- Using `[ ]` to define a character range doesn't work
