er 

# Level-1

## Given Details --

	  > Password is in a file called "readme" in home directory
	
	  > Username is bandit1 for level one 


## Goal -- 
	 - Find the password in level-0 for level-1


## Commands Needed --

	 ls, cd, cat, file, du, find.

## Theory --

## ls --
	ls stands for 'list' used in listing directory contents.


#### Syntax --

	ls <flag> 
	{YOU CAN ALSO USE THE 'ls' COMMAND WITHOUT ANY FLAG IT WILL JUST LIST THE FILES AND FOLDERS OF THE DIRECTORY}
    
     {ALSO A DIRECTORY IS JUST THE FOLDER YOU ARE ON, & A WORKING DIRECTORY IS JUST THE FOLDER YOU ARE WORKING ON}


#### Flag -- 

	-a: to list all files, including hidden one.
	-ls: to list the files in a format where you can see (permissions, ownership, size, modification date).
	-lh: for human readable sizes like (KiB, MiB, GiB).
	-lSR: for long format, sorted by sizes in descending order.
	-ltr: long format, sorted by time the file modified in reverse order(oldest first).




## cd --
	 Change the current working directory.


#### Syntax --

	 cd path/to/directory
	 
	 {you can also just use 'cd' to go to home directory of current user}


#### Flag --

	-cd .. : to go up to the parent directory
	-cd ~username : to go to home directory of specified user
	-cd - : for previously chosen directory
	-cd / : to go to root directory


## cat --

	Cat prints and concatenate files.

#### Syntax -- 

	cat <option> file/<path-to-file>


- Now i won't be writing (path-to-file) again and be using just file but you can use the path to determine the file, it would be to use the path when file is in different directory.

#### Flags --

	> [cat file1 file2 > file3]
		to merge the output of two different files and make one file with those two files content. 
	
	> [cat file1 file2]  
		 to merge the content of the two files and display it in the terminal.
	
	> [cat > file] 
		 write the content of the file inside the terminal without any text editor 	
	
	> cat -n file 
		to number the output lines
	
	 > cat -A file
		 to list all the characters, with tabs, ending, & non-printing characters.
	
	> cat file | program (grep)
		 pipe/vertical bar '|' for piping the commands like, list listing the file content and then using grep to search the specific key word 
		 eg -> cat crash-report.log | grep "launch_error"


## file --

	 file command output the type of file is it. it does not care about the extension or filename of the file, Instead it examines the content of the file like its "magic bytes" or signature. 

#### Syntax --

	file <options> path/to/file or FILE

#### Description -- 

	 like a .txt file outputs > notes.txt: ASCII text
	 - .png outputs > image.png: PNG image data etc. 
	 - .mp3 outputs > song.mp3: MPEG ADTS, layer III
	
	it can even identify -- 
		- PDFs
		- ZIP archives
		- Shell scripts
		- Python scripts
		- ELF executables
		- Shared libraries
		- Device files


#### Flag -- 

	-b: to output the brief like just the description not the file name 
	
	-z: to look inside the file to get detail about the files inside the file like zip, and works for formats like gzip, bzip2, xz. 
	
	-i: to show the MIME type , it is a standard format used by browser, email clients, servers to identify file type.

| File  | MINE type       |
| ----- | --------------- |
| .txt  | text/plain      |
| .html | text/html       |
| .png  | image/jpng      |
| .pdf  | application/pdf |


## du --

	stand for "disk usage", it estimate how much disk space and directories are using.
	 
	 Think of it this way:

	- `ls` tells you **what exists**.
	- `file` tells you **what kind of file it is**.
	- `du` tells you **how much disk space it uses**.


#### Syntax -- 

	du <options> or file/directory

#### Flag -- 

	-b, k, m, BG shows the space in different sizes like 
	
		-b: shows bytes
		-k: shows kilo bytes(KiB)
		-m: shows mega bytes(MiB)

	-h: flag that converts output to human-readable and adds respective KB,MD or GB sizes in the output to the respective files or directory so dont have to specifie the size and get convenience like the b,k,m,BG flags roundup the size for a 2.4 G directory it may show 3G so "-h" flag shows most precise value.

	-sh: combination of "-s" to summarize(only the total) and "-h" to make output human-readable 

	-ah: normally du ignores the files in the directory, but with this flag it list all the files with the size in the directory.
		(it is also a combination of -a(all files) & -h(you know))

	-d: adds the limit to the directories depth, it tells du how many levels of sub-directories to include in the output.

		SYNTAX : du -d n  
	
			du -h -d 1 <directory> : tell to include first level of sub-directory.
			du -h -d 2 <directory> : same to add second level of sub-directory. 


## find -- 

	Find files or directories under a directory tree, recursively.

#### Syntax -- 

	find <path/to/directory or file> <option>


#### Flags -- 

{ in the examples the '* ' (wildcard) means any character like file name you given to yours } 

	-find <directory> -name "*.ext" : find by extension. like find .ext file in the current directory and its sub-directory.


	-find <directory> -path "path/of/directory .ext -or -name "*pattern*" : flags to find by path or name pattern this "-or" tells to find either one of the two
	
		-path--> math the file's full path
		-or--> either condition can match btw options
		-name--> mathches the filename


	-find <directory> -type d -iname "*lib*" : find the file/directory by their name including word in this "*xyz*" 
		
		-type d: means whose name contain lib (in this example)
		-iname: tell to ignore uppercase/lowercase


	find <directory> -name "*.py" -not -path "*/directory-name/*"
	
		means find all .py files except inside *directory-name*


	find <directory> -maxdepth 1 -size +500k -size -10M
	
		means find file between 500 KB and 10 MB.
	
		-maxdepth 1 --> search only in the current directory, not in sub-directories.
	
		+500K --> find larger than 500 KB
		-10M --> find smaller than 10 MB




## Walk-through -- 

- First step is to connect to the level 0 using ssh , remember the username, password & host  for connecting to the remote machine and dont forgot to add port 

- After you login to the level zero the interface would look like this 






- Now we need to run commands like we use to connect to the server and also you can check we are in right level by reading the first name which is the username represent in shell prompt in linux 

- So we are in the home directory you can check it with a linux command which is (pwd) that lists current directory and we are in home and under home we are in bandit0 

- Now we need command that lists files and directory(folders) in the current directory

- Then we get the file we need we can inspact the file more by a command that displays file type , and commad that gives how much it occupies the space but it is not need we need these command in future but now a command that will output the content of the file try yourself and run it 

- i got it and i hope you also. 
