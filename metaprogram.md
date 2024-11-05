## Metaprogramming

Set of things that are more about process than they are about writing code or working more efficiently.
* look at systems for building and testing your code, and for managing dependencies



### Build Systems
For most projects, whether they contain code or not, there is a “build process”. These are usually called “build systems”, and there are many of them. Which one you use depends on the task at hand, your language of preference, and the size of the project.

At their core, they are all very similar though. **You define a number of dependencies, a number of targets, and rules for going from one to the other.** 


`Make` is one of the most common build systems out there, and you will usually find it installed on pretty much any UNIX based computer

When you run make, it consults a file called Makefile in the current directory. All the targets, their dependencies, and the rules are defined in that file

For example:
``` bash

paper.pdf: paper.tex plot-data.png
	pdflatex paper.tex

plot-%.png: %.dat plot.py
	./plot.py -i $*.dat -o $@

```

the things named on the right-hand side are dependencies, and the left-hand side is the target
* the indented block is a sequence of programs to produce the target from those dependencies

The ‘%’ in a rule is a “pattern” and will match the same string on the left and on the right
if the target plot-foo.png is requested, make will look for the dependencies foo.dat and plot.py

**The special thing about make is that it checks for all the previously built targets were still up to date with respect to their listed dependencies**



## Dependency Management
At a more macro level, your software projects are likely to have dependencies that are themselves projects
* You might depend on installed programs (like python), system packages (like openssl), or libraries within your programming language

Common terminology when working with repositories
* versioning - most projects that other projects depend on issue a version number with every release. Usually something like `8.1.3` or `64.1.20192004`.

But what if you issue a security update which does not change the public interface of my library and any version before it should start using?


The common standard is semantic versioning. With semantic versioning, every version number is of the form: major.minor.patch
* If a new release does not change the API, increase the patch version.
* If you add to your API in a backwards-compatible way, increase the minor version.
* If you change the API in a non-backwards-compatible way, increase the major version.


When working with dependency management systems, you may also come across the notion of lock files
- A lock file is simply a file that lists the exact version you are currently depending on of each dependency

There are many reasons for this, such as avoiding unnecessary recompiles, having reproducible builds, or not automatically updating to the latest version (which may be broken)

