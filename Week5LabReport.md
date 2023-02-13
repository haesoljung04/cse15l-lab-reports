# Week 5 Lab Report
## Researching Commands: `grep`
- **Using `-r` option**
- Sources used: ChatGPT and [grep man page](https://linuxcommand.org/lc3_man_pages/grep1.html)<br />
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
- Sources used: ChatGPT and [grep man page](https://linuxcommand.org/lc3_man_pages/grep1.html)
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
> Explanation: the `grep -l` option allows us to print the names of the files that contain a match\
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
> Explanation: the use of `--exclude=` allows us to exlude certain types of files by specifying file
> types in braces. In this case we exclude our search from `{jpg,png}` files. This is useful if you are
> looking for certain types of files.



- **Using `-n` option**
- Sources used: ChatGPT and [grep man page](https://linuxcommand.org/lc3_man_pages/grep1.html)
1.
```
[cs15lwi23atp@ieng6-202]:skill-demo1-data:287$ grep -n Emperor written_2/travel_guides/berlitz2/Vallarta-WhereToGo.txt
18:The best known image of Puerto Vallarta is the Iglesia de Guadalupe (Guadalupe Church), dedicated to the Virgin of
Guadalupe, and topped by a copy of the crown worn by Empress Carlota in the 1860s. Wife of Emperor Maximillian
```
> Explanation: the `grep -n` option allows use to search for a specific pattern in a file and print the line numbers of
> the matching lines. This is useful because if we know the file that has a specific pattern like `Emperor` we are able
> to get the exact line number in which it appears using this command. 
2.
```
[cs15lwi23atp@ieng6-202]:skill-demo1-data:289$ grep -rn Hooters written_2
written_2/travel_guides/berlitz2/Vallarta-WhatToDo.txt:17:Also downtown, you’ll find the imported Hard
Rock Café, Planet Hollywood, and Hooters, but they tend to draw lesser crowds than the locally-owned options.
written_2/travel_guides/berlitz2/Vallarta-WhereToGo.txt:18:This plaza is representative of plazas throughout 
Mexico; what reminds you that you are in an international tourist town are the surrounding signs for Burger King, S
ubway, and Hooters.
```
> Explanation: the combination of `grep -r` and `grep -n` in `grep -rn` combines the best of both worlds and allows us to
> search for all the lines in all the files of `written_2` that have the word `Hooters`. This would be useful in a
> situation where we have to find all the lines in all the files of a directory that contain a pattern.



- **Using `-o` option**
- Sources used: ChatGPT and [grep man page](https://linuxcommand.org/lc3_man_pages/grep1.html)
1.
```
[cs15lwi23atp@ieng6-202]:skill-demo1-data:299$ grep -o balloon written_2/travel_guides/berlitz2/Vallarta-WhereToGo.txt
balloon
```
> Explanation: the `grep -o` command at its simplest prints the text that matches the specified pattern which is `balloon`
> in this case. This is useful because it basically performs the default `grep` command but keeps it simple by only
> outputting the text if it exists.
2.
```
[cs15lwi23atp@ieng6-202]:skill-demo1-data:297$ grep -o \b[b][a-z]* written_2/travel_guides/berlitz2/Vallarta-WhereToGo.txt 
balconies
back
bars
```
> Explanation: the `grep -o` command extracts the matching text from a file and prints it to the console. Here, we
> use this command along with the expression `\b[Aa][a-z]*` to find all the words that start with a lowercase b in
> the given file. This is useful because it allows us to use a more broad pattern than searching for a single word.
