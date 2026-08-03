# Level: 5 → 6

# Given Details --

- The password for level 6 is stored in a file inside the `inhere` directory
- The file is exactly 1033 bytes in size
- The file is human-readable (not binary)
- The file is NOT executable


# Goal --

- Find the one file, buried somewhere inside `inhere`, that matches all three given facts: 1033 bytes, human-readable, non-executable — and read the password from it.


# Commands Needed --

	ls, cd, cat, du, find, file


# Theory --

## Filtering by file size with `find` --

	`find` can filter directly by size using the `-size` flag, instead of 
	you having to check each file manually.

#### Syntax:   find <path> -size <number><unit>

	The unit matters — "c" means bytes, "k" means kilobytes, "M" means 
	megabytes. Since this level gives an exact byte count, "c" is what 
	you need.


## Filtering by permissions with `find` --

	`find` can also filter by whether a file is executable, using 
	`-executable`. Prefixing it with "!" negates the condition — meaning 
	"find files that are NOT executable."

#### Syntax:   find <path> ! -executable


## Alternative: `du` combined with `grep` --

	`du` reports disk usage per file. Combined with a flag that shows 
	every file (not just folders) and a byte-accurate output, you can 
	pipe the result into `grep` and filter for the exact size given.

#### Syntax:   du -ab -d <depth> | grep "<size>"


## Walk-through --

	- With a clean terminal, SSH into bandit5 using the password you 
	  found in the Level 4 → 5 writeup.

	- List the contents of the home directory, then move into `inhere`. 
	  You'll find a maze of nested folders, not a flat list of files 
	  this time.

	- Think about the three facts given: exact size, human-readable, 
	  and non-executable. You don't need to open every file to check 
	  all three by hand — `find` can filter by size and permissions 
	  directly, and `file` can confirm readability without you needing 
	  to cat anything first.

	- Try filtering by size alone first, and see how many results come 
	  back. If more than one file matches, think about which of the 
	  other two facts (human-readable, non-executable) you can use to 
	  narrow it down further.

	- There's more than one valid way to combine these filters — try 
	  building the filter yourself before checking the alternate methods 
	  above.

	- Once you've narrowed it down to a single file, read its contents 
	  the same way you have in previous levels.

![Password file identified inside nested maybehere folders, contents redacted](../images/level5-to-6-checkpoint1.png)