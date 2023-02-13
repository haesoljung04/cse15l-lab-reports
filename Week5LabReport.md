# Week 5 Lab Report
## Researching Commands: `grep`
- Using `-r` option
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
> the `--include` option allows use to specify the file extension to search in. In this case, we
> only want to search in txt files so we put `*.txt`.

