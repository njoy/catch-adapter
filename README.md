# catch-adapter
A repository which adapts the [Catch](https://github.com/catchorg/Catch2) Unit Test project for use in the NJOY21 build scheme.

## Git Subtree
This repository uses a git subtree for the directory `src`. The remote from which the subtree is made is located at [https://github.com/catchorg/Catch2.git](https://github.com/catchorg/Catch2.git). Equivalently, you can use the ssh location at `git@github.com:catchorg/Catch2.git`.

To facilitate updating the subtree when it gets updated upstream, do the following:

```bash
# This only needs to be done once
git remote add catch https://github.com/catchorg/Catch2.git

# Do this when you need to update the subtree
git subtree pull --prefix=src catch Catch1.x --squash
```

# License
The code contained in this directory is covered by the license contained in the [LICENSE](LICENSE) file. The code contained in the `src` directory is contained in its own [LICENSE](src/LICENSE_1_0.txt).

