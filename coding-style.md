# Coding Style

These are general coding style guidelines we've adopted for my research group.

**Background on UNIX command-line options:**
Many (most?) UNIX style command-line options have "long form" and a "short form", where the latter is a single character.
For example `-a` and `--all` for `ls` (although, interestingly, `-l` doesn't have a long form).

Short form options can be strung together, e.g., `ls -l -a` becomes `ls -la`.
Thus `--abc` and `-abc` mean very different things; the first represents a single option, the second is a shorthand for multiple options, e.g., `-a -b -c`.

## General

+ We use a maximum line length of 120 character.
The rationale for this limit is that 120 is (approximately) the number of characters that will render in GitHub without horizontal scrolling.
This maximizes use of screen real estate.

## Python

+ We adopt [PEP8](https://pep8.org/).
+ We adopt single quotes `'` for strings; unless another approach is obviously better, we use [f-strings](https://www.python.org/dev/peps/pep-0498/) for formatting.
+ We adopt the [numpy docstring style](https://numpydoc.readthedocs.io/en/latest/format.html).

**Command-line options:** We try to stay true to the UNIX convention, which is what `argparse` (implicitly) endorses anyway.
This means that Java and Python counterparts of script that do the same thing will have different parameters.
Thus:

+ Options begin with two dashes: `--index` instead of `-index`.
+ Use single dash (instead of underscore) for multi-token options: `--max-value` instead of `-max_value`.
+ Use `.` to group parameters, e.g., `--bm25` (use BM25) and `--bm25.b` (set the BM25 _b_ parameter). I think this is less confusing than `--bm25-b`.


## Java

+ Two space indent, otherwise standard conventions.

**Command-line options:** Java breaks the UNIX convention and is a total mess.
For example, `-classpath` and `--class-path` both work (although the first is much more common).
For command-line programs written in Java, we try to maintain consistency to Java options:

+ Options begin with a single dash: `-index` instead of `--index`.
+ Use camel case instead of snake case: `-maxValue` instead of `-max_value`.
+ Use `.` to group parameters, e.g., `-bm25` (use BM25) and `-bm25.b` (set the BM25 _b_ parameter).