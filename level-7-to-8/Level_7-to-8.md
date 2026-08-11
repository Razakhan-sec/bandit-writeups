## Level: 7 → 8

# Given Details --

- The password for level 8 is stored in a file called `data.txt`
- The password is located next to the word `millionth`, somewhere inside that file
- Username for this level: bandit7

# Goal --

- Find the password for level 8, which sits right next to the word "millionth" inside `data.txt`.

# Commands Needed --

```
man, grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd
```

# Theory --

## man --

```
man is short for manual, and its basically the built in guidebook for almost every command on linux. if your need to know what this command does or what flags it uses, `man <command>` will give its full documentation right in the terminal, without any internet.
```

#### Syntax: man {command}

## grep --

```
grep searches through texts and prints out any line that matches a pattern you give to it. its one of the most useful commands to find keywords, since most of the time your not going though the whole file for one specific word or line buried inside it.
```

#### Syntax: grep "pattern" filename

> ⚠️ **Common mistake:** Forgetting to quote the pattern can cause issues if it contains spaces or special characters — the shell will try to split it up like it does with --filenames with spaces--.

## sort --

```
sort takes the lines of a file and arranges them, alphabetically or numerically depending on the flags you used. usefull for making sense in a big messy file, or for prepping data before you run uniq on it (since uniq only catches duplicates that are next to each other).
```

#### Syntax: sort {filename}

## uniq --

```
uniq filters out repeated lines that are right next to eachother, its often used right after sort, together they let you find lines that only appear once, or count how many times each line shows up.
```

#### Syntax: uniq {filename} (usually piped after sort, like: sort {filename} | uniq )

## strings --

```
strings pulls out anything that looks like readable text from a file, even if the rest of the file is binary garbage. really usefull when peeking inside compiled programs or weird file types where cat would just print gibberish to your screen.
```

#### Syntax: strings {filename}

## base64 --

```
base64 does encoding, not encryption, it takes binary data and turns it into plain text characters so it can be safely copied or sended somewhere that only handles text. the base64 command can both encode a file into this format and decode it back to the original.
```

#### Syntax: base64 {filename} (to encode) / base64 -d {filename} (to decode)

## tr --

```
tr stands for translate, it replaces or deletes characters from text as it passes through. its often used to swap one character to another across an entire file or stream, like turning all uppercase letters into lowercase, or stripping out unwanted characters entirely.
```

#### Syntax: tr {'set1'} {'set2'}

## tar --

```
tar bundles multiple files and folders into a single archive file, commonly giving a .tar. by itself tar doesnt compress anything, it just packages everything together, thats what the -c (create) and -x (extract) flags are mainly for.
```

#### Syntax: tar -xvf {filename.tar}   (to extract)  and  tar -cvf {filename}.tar {files}   (to create)

## gzip --

```
gzip is a compression tool, it shrinks a single file down and usually leaves it with a .gz extension. its often paired with tar since tar handles the bundling and gzip handles the shrinking, together you get the familiar .tar.gz files.
```

#### Syntax: gzip {filename}    (to compress) / gzip -d {filename}.gz    (to decompress)

## bzip2 --

```
bzip2 does basically the same job as gzip, compressing files, but it uses a different algorithm thats usually a bit slower though it can compress tighter. files compressed with it end in .bz2, and you'll see them paired with tar the same way, giving .tar.bz2.
```

#### Syntax: bzip2 {filename}    (to compress) / bzip2 -d {filename}.bz2    (to decompress)

## xxd --

```
xxd converts a file into a hex dump, showing you the raw bytes of a file in hexadecimal alongside their readable ascii equivalent (where possible). its useful for looking at a files actual raw content when you need to see whats really there instead of how it gets displayed.
```

#### Syntax: xxd {filename}


## Walkthrough:

### Checkpoint 1: Grepping for the right line

![Terminal showing grep output for the word millionth in data.txt, password redacted](../images/level7-8_checkpoint1.png) _After logging into bandit7, theres no need to open `data.txt` and scroll through it manualy — grep can search the whole file in one go for the word "millionth" and print only the matching line, which is the line with the password sitting right next to it._