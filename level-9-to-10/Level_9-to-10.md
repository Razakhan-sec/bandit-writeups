## Level: 9 → 10

# Given Details --

- The password for level 10 is stored in the file `data.txt`
- The password is one of the few human readable strings in the file, and its preceded by several `=` characters
- Username for this level: bandit9

# Goal --

- Find the human readable string inside `data.txt` thats preceded by a bunch of `=` signs, and grab the password sitting next to it.

# Commands Needed --

```
strings, grep
```

# Theory --

## strings --

```
data.txt in this level isnt a normal text file, its mostly binary garbage with a few actual readable bits mixed in. cat-ing it directly would just spam your terminal with junk characters and possibly mess up how it displays stuff after. strings fixes that by pulling out only the parts of a file that look like actual printable text and ignoring everything else, so you only see whats actually readable.
```

#### Syntax: strings filename

#### Common flags --

```
-n      sets the minimum length a string has to be before its printed (so short random junk that happens to look like text gets filtered out)
-a      scans the entire file, not just certain sections (usefull for object/binary files that have sections strings normally skips)
-t      shows the offset of where each string was found in the file (x for hex, o for octal, d for decimal)
```

> ⚠️ **Common mistake:** running plain `strings data.txt` with no `-n` flag still works, but it dumps out alot of short garbage strings along with the real one, making it harder to spot the password among the noise.

## Walkthrough:

### Checkpoint 1: Listing the home directory

![Home directory listing showing data.txt](../images/level9-10_checkpoint1.png) _After loging into bandit9, list whats in the home directory. Same as last level theres just the one file, `data.txt`, but this time its mostly binary data instead of plain repeated lines._

### Checkpoint 2: Pulling out the readable strings

![Terminal output of strings -n 32 on data.txt, showing the password redacted](../images/level9-10_checkpoint2.png) _Running `strings` with the `-n 32` flag filters out anything shorter then 32 characters, which cuts out basically all the junk and leaves behind only the handful of strings that are actually long enough to matter. The line of equal signs followed by the password is one of the very few things left standing._