
# Data Wrangling
To have data in one format and transform to another format. To wrangle data, we need two things: data to wrangle, and something to do with it


The `sed` is a stream editor that builds on top of the old `ed` editor. 
Short commands for how to modify the file, `s` command is written on the form: `s/REGEX/SUBSTITUION/`

## Regular Expressions
Regular expressions are common ,here are some very common patterns:
* `.` means “any single character” except newline
* `*` zero or more of the preceding match
* `+` one or more of the preceding match
* `[abc]` any one character of a, b, and c
* `(RX1|RX2)` either something that matches RX1 or RX2

Well, `*` and `+` are, by default, “greedy”. They will match as much text as they can. In some regular expression implementations, you can just suffix * or + with a ? to make them non-greedy

## More Wrangling
Another command that is helpful for data wrangling is `sort` and `uniq`
- Command `uniq -c` will collapse consecutive lines that are the same into a single line and count number of occurrences

Another command is `awk`
- Column-based stream processor, more focused on columned data

For example  ```awk ‘{print $2}’ | paste -sd```, this prints out the second column

`awk` programs take the form of an optional pattern plus a block saying what to do if the pattern matches a given line.
> [!TIP]
> Awk is a programming language


## Analyzing data
There are other tools such as `bc`, a calculator that can from STDIN

Arguments wrangling
- Sometimes you want to do data wrangling to find things to install or remove based on some longer list
- `xargs` can be a powerful tool

The xargs takes of lines of input and turns them into arguments
``` bash
rustup toolchain list | grep nightly | grep -vE "nightly-x86" | sed 's/-x86.*//' | xargs rustup toolchain uninstall
```


## Exercises
Exercise 1: Find the number of words (in /usr/share/dict/words) that contain at least three as and don’t have a 's ending. What are the three most common last two letters of those words? 

`sed -E -n "/.*a.*a.*a[^'s]$/p" /usr/share/dict/words | awk '{for (i=1; i<=NF; i++) print substr($i, length($i)-1, 2)}' | sort | uniq -c | sort -nk1,1 | tail -n 3`

Exercise 2: Redirecting output to same file? It is not unique to sed; it applies to other command-line tools and scripts where output redirection is used. If you overwrite a file while simultaneously trying to read from it, you face similar risks of data corruption or loss.

> [!WARN]
> DO NOT DO sed s/REGEX/SUBSTITUTION/ input.txt > input.txt

Exercise 3: For the exercise on mls.csv I used 

`awk -F, '{ print $6, $7 }' mls.csv | tail -n + 2`




