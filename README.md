# Issues and Fixes

# .gitignore

## unable to ignore files even after adding into **`.gitigore`** file

There could be several reasons why your `.gitignore` file is not ignoring certain files.
Here are a few possibilities:
-The files were already added to your repository before you added them to your `.gitignore` file. Adding files to `.gitignore` does not remove them from the repository. To remove them, you need to run git rm --cached <file> for each file.
-You may have specified the wrong path or filename in your `.gitignore` file. Double-check that the paths and filenames are correct, and that they match the files you want to ignore.
-Git may be ignoring your `.gitignore `file. Check that your `.gitignore` file is in the root of your repository and that its filename is spelled correctly. If Git is still ignoring your `.gitignore` file, you can force it to read the file by running git add -f `.gitignore`.
-The files you want to ignore may already be tracked by Git. In this case, you need to remove them from the repository and commit the changes. You can do this with the following commands:

```shell
git rm -r --cached .
git add .
git commit -m "Removed files from repository"

```


