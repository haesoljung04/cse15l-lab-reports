# Week 5 Lab Report
## Researching Commands: `grep`
- **Using `-r` option**
1.
```
[cs15lwi23atp@ieng6-202]:skill-demo1-data:268$ grep -r jetfoil written_2
written_2/travel_guides/berlitz1/WhereToHongKong.txt:\        
The easiest way to get to Macau is by jetfoil, operated by
```
> Explanation: the `grep -r` command followed by a pattern searches recursively for that pattern
> in all the files of a directory and its subdirectories. In the code block above, we can see 
> that this is useful when we would like to find the file that contains a specific word. 
2.
```
[cs15lwi23atp@ieng6-202]:skill-demo1-data:272$ grep -r "Bixiaci" --include=*.txt written_2\
written_2/travel_guides/berlitz2/China-WhereToGo.txt:On the summit there are even more treasures.\ 
The Tang Dynasty Rock Inscriptions (Moyabei) were struck in large gold-foil characters to record\ 
Emperor Xuanzong’s imperial pilgrimage in the year 726. The Stele Without Inscription (Wuzibei)\ 
is blank, thought to have been placed here by the First Emperor over 2,000 years earlier; everyone\ 
who reaches it must touch it for good luck. The Temple of the Purple Dawn (Bixiaci)
```
> Explanation: This variation of the `grep -r` command will also search for the given pattern but
> the `--include` option allows us to specify the file extension to search in. In this case, we
> only want to search in txt files so we put `*.txt`. This is useful because we can tell the computer
> we only want to see text files.

- **Using `-l` option**
1.
```
[cs15lwi23atp@ieng6-202]:skill-demo1-data:285$ grep -rl Hawaii written_2
written_2/travel_guides/berlitz1/HandRHawaii.txt
written_2/travel_guides/berlitz1/HistoryHawaii.txt
written_2/travel_guides/berlitz1/HistoryMalaysia.txt
written_2/travel_guides/berlitz1/WhatToHawaii.txt
written_2/travel_guides/berlitz1/WhereToHawaii.txt
written_2/travel_guides/berlitz2/Bahamas-Intro.txt
written_2/travel_guides/berlitz2/California-History.txt
written_2/travel_guides/berlitz2/California-WhatToDo.txt
```
> Explanation: the `grep -l` option allows use to print the names of the files that contain a match\
> for the specified pattern. here we use `grep -rl` in order to search recursively in `written_2` and\
> print just the name of the file that has the word `Hawaii`. This option is useful because it lets
> us just see the file names and not have all this messy text in front of us.

2. 
```
[cs15lwi23atp@ieng6-202]:skill-demo1-data:286$ grep -rl Emperor --exclude=*.{jpg,png} written_2
written_2/travel_guides/berlitz1/HistoryFrance.txt
written_2/travel_guides/berlitz1/HistoryGreek.txt
written_2/travel_guides/berlitz1/HistoryHongKong.txt
written_2/travel_guides/berlitz1/HistoryIndia.txt
written_2/travel_guides/berlitz1/HistoryIstanbul.txt
written_2/travel_guides/berlitz1/HistoryItaly.txt
written_2/travel_guides/berlitz1/HistoryJapan.txt
```
> Explanation: the use of `--exclude=` allows use to exlude certain types of files by specifying file
> types in braces. In this case we exclude our search from `{jpg,png}` files. This is useful if you are
> looking for certain types of files.

- **Using `n` option**
1.
```
[cs15lwi23atp@ieng6-202]:skill-demo1-data:287$ grep -n Emperor written_2/travel_guides/berlitz2/Vallarta-WhereToGo.txt
18:The best known image of Puerto Vallarta is the Iglesia de Guadalupe (Guadalupe Church), dedicated to the Virgin of
Guadalupe, and topped by a copy of the crown worn by Empress Carlota in the 1860s. Wife of Emperor Maximillian
```
> Explanation: the `grep -n` option allows use to search for a specific pattern in a file and print the line numbers of
> the matching lines. This is useful because if we know the file that has a specific pattern like `Emperor` we are able
> to get the exact line number in which it appears using this command. 
