# Automaticly run Laravel Pint when commiting changes

Guide: https://laraveldaily.com/post/laravel-pint-pre-commit-hooks-github-actions

Create a file .git/hooks/pre-commit with the following content:

```
nano .git/hooks/pre-commit
```

Then paste this into the file
```
#!/bin/sh
files=$(git diff --cached --name-only --diff-filter=ACM -- '*.php');
vendor/bin/pint $files -q
 
git add $files
```

Then run to correct the permissions
```
chmod a+x .git/hooks/pre-commit
```

This works only locally, doesn't get pushed to github.
