# Week 9 Lab Report(Lab Report 5)
## Researching Commands: `find`
- **Using `-name` option**
- Sources used: ChatGPT and [find man page](https://docs.oracle.com/cd/E86824_01/html/E54763/find-1g.html)<br />
1.
Command:
```
[cs15lwi23atp@ieng6-202]:written_2:492$ find -name "*China*"
```
Output:
```
./travel_guides/berlitz2/China-History.txt
./travel_guides/berlitz2/China-WhatToDo.txt
./travel_guides/berlitz2/China-WhereToGo.txt
```
> Explanation: the `find -name` command followed by a pattern searches recursively for that pattern in all the files of the current directory and its subdirectories. 
> In the code block above, we can see that this is useful when we would like to find the file that contains a specific word. It is also important that the word is 
> surrounded by `*` to isolate the pattern.
<br />

2.
Command:
```
[cs15lwi23atp@ieng6-202]:docsearch:498$ find written_2 -name "*China*"
```
Output:
```
written_2/travel_guides/berlitz2/China-History.txt
written_2/travel_guides/berlitz2/China-WhatToDo.txt
written_2/travel_guides/berlitz2/China-WhereToGo.txt
```
> Explanation: This variation of the `find -name` command will also search for the given pattern but this time we include the name of the directory we want to seach 
> in, which in this case is `written_2`. This is useful because we can specify the bounds for what directories we want to search in.
<br />

- **Using `-type` option**
- Sources used: ChatGPT and [find man page](https://docs.oracle.com/cd/E86824_01/html/E54763/find-1g.html)<br />
1.
Command:
```
[cs15lwi23atp@ieng6-202]:written_2:494$ find -type d
```
Output:
```
.
./non-fiction
./non-fiction/OUP
./non-fiction/OUP/Abernathy
./non-fiction/OUP/Berk
./non-fiction/OUP/Castro
./non-fiction/OUP/Fletcher
./non-fiction/OUP/Kauffman
./non-fiction/OUP/Rybczynski
./travel_guides
./travel_guides/berlitz1
./travel_guides/berlitz2
```
> Explanation: the `find -type` option allows us to print the names of the files/directories that match the specified type. here we use `d` in order to search 
> recursively in the current directory and print just the names of the directories. This option is useful because it lets us classify and sort through the computer 
> by directories.
<br />

2.
Command:
```
[cs15lwi23atp@ieng6-202]:written_2:502$ find -type f
```
Output:
```
./non-fiction/OUP/Abernathy/ch1.txt
./non-fiction/OUP/Abernathy/ch14.txt
./non-fiction/OUP/Abernathy/ch15.txt
etc....
```
> Explanation: Here we use `f` instead of `d` in order to search in the current directory for files not directories. This option is useful because it lets us classify 
> and sortthrough the computer by files.
<br />

- **Using `-size` option**
- Sources used: ChatGPT and [find man page](https://docs.oracle.com/cd/E86824_01/html/E54763/find-1g.html)<br />
1.
Command:
```
[cs15lwi23atp@ieng6-202]:written_2:514$ find -size -2k
```
Output:
```
./travel_guides/berlitz1/HandRIbiza.txt
./travel_guides/berlitz1/HandRIstanbul.txt
```
> Explanation: the `find -size` option allows use to search for files based on a specified size argument. This is useful because if we want to look at
> files that are only a certain size so we can do tasks more efficiently then this command is perfect. In this case, we use `-2k` to specify we only
> want to look at file that are less than 2 kilobytes.
<br />

2.
Command:
```
[cs15lwi23atp@ieng6-202]:written_2:525$ find -size +200k
```
Output:
```
./travel_guides/berlitz1/WhereToFrance.txt
./travel_guides/berlitz1/WhereToItaly.txt
./travel_guides/berlitz2/Canada-WhereToGo.txt
```
> Explanation: Here we are doing the same thing as above but instead we modify the `-` to be a `+ ` which allows us to look at files that are bigger than 
> the specified size argument. If we happened to want to delete unnecessarily large files from the computer this option would be essential. In this case, 
> I was able to isolate 3 `.txt` files that were bigger than 200 kilobytes.
<br />

- **Using `-printf` option**
- Sources used: ChatGPT and [find man page](https://docs.oracle.com/cd/E86824_01/html/E54763/find-1g.html)<br />
1.
Command:
```
[cs15lwi23atp@ieng6-202]:written_2:534$ find -type f -printf "%f\n"
```
Output:
```
HandRHawaii.txt
HandRHongKong.txt
HandRIbiza.txt
HandRIsrael.txt
etc...
```
> Explanation: the `find -printf` command at its simplest provides a way for us to format the results of `find`. In this case we print only the names of the files
> in `written_2` by using the formatter `"f\m"`. This is useful because sometimes I just do not want to see the path names.

<br />

2.
Command:
```
[cs15lwi23atp@ieng6-202]:written_2:535$ find -type f -printf "%f\t%s\n"
```
Output:
```
HistoryFrance.txt       38509
HistoryGreek.txt        18666
HistoryHawaii.txt       16522
```
> Explanation: Here we do the exact same thing but we use a different formatter by including `%s` which basically tells `find` to print the size of the file
> in bytes. This can be very useful if you want to see which files are bigger or smaller without all the complicated paths and extra information.
