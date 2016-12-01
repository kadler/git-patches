# git-patches
IBM i specific Git patches for Git 2.10

This repository contains a set of branches that correlate with a major Git release. Each branch contains a set of directories that correlate with an IBM i release and a directory ```any``` that applies to all IBM i releases.

The way to use this repository is:
- clone the branch specific to your version of Git
- copy the patches from ```any``` to the Git source directory
- copy the patches from the directory specific to your IBM i release to the Git source directory
- Apply each patch with ```patch -p1```

Example: Compiling Git 2.8.3 on IBM i 7.1

```
tar -xzf git-2.8.3.tar.gz
git clone -b 2.8 --single-branch https://github.com/kadler/git-patches.git patches
cd git-2.8.3
cp ../patches/any/*.patch .
cp ../patches/7.1/*.patch .
for f in *.patch
do
  patch -p1 < $f
done
```
