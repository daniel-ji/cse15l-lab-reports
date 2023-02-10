# CSE 15L, LAB 3

## Chosen command: `grep`

### Source for all options: https://www.geeksforgeeks.org/grep-command-in-unixlinux/

Note: Before running these commands, globstar was enabled, which is why the `**` is used in the commands. Globstar is a bash option that allows for recursive globbing. For example, `**/*.java` will match all files with the `.java` extension in the current directory and all subdirectories. It was enabled with the command `shopt -s globstar`.

Note: I did not use ChatGPT for this assignment, but I did explore Github Copilot. It was helpful for auto-completing sections of text of this report, and I would definitely use it again.

***

### Command Line Option 1: `grep -c`

The -c flag is used to count the number of lines that match the pattern. This is useful when you want to know how many lines match a certain pattern, but don't want to see the lines themselves.

**Example 1:** 

Command: `grep -c "Europe" travel_guides/berlitz2/**/*.txt`

Output: 
```
travel_guides/berlitz2/Algarve-History.txt:5
travel_guides/berlitz2/Algarve-Intro.txt:4
travel_guides/berlitz2/Algarve-WhatToDo.txt:3
travel_guides/berlitz2/Algarve-WhereToGo.txt:8
travel_guides/berlitz2/Amsterdam-History.txt:7
travel_guides/berlitz2/Amsterdam-Intro.txt:3
travel_guides/berlitz2/Amsterdam-WhatToDo.txt:3
travel_guides/berlitz2/Amsterdam-WhereToGo.txt:4
travel_guides/berlitz2/Athens-History.txt:4
travel_guides/berlitz2/Athens-Intro.txt:2
travel_guides/berlitz2/Athens-WhatToDo.txt:4
travel_guides/berlitz2/Athens-WhereToGo.txt:5
travel_guides/berlitz2/Bahamas-History.txt:3
travel_guides/berlitz2/Bahamas-Intro.txt:0
travel_guides/berlitz2/Bahamas-WhatToDo.txt:1
travel_guides/berlitz2/Bahamas-WhereToGo.txt:1
travel_guides/berlitz2/Bali-History.txt:1
travel_guides/berlitz2/Bali-WhatToDo.txt:0
travel_guides/berlitz2/Bali-WhereToGo.txt:4
travel_guides/berlitz2/Barcelona-History.txt:7
travel_guides/berlitz2/Barcelona-WhatToDo.txt:4
travel_guides/berlitz2/Barcelona-WhereToGo.txt:3
... and more, but you get the idea
```

Explanation: The command `grep -c "Europe" travel_guides/berlitz2/**/*.txt` searches for the text "Europe" in all text files in the directory `travel_guides/berlitz2/` and all subdirectories, as specified by the globstar and the *.txt patterns, respectively. The `-c` flag counts the number of matches and only shows the number of matches in each file without the actual matches within the files (which would have showed up without the `-c` flag). For example, the file `travel_guides/berlitz2/Barcelona-WhatToDo.txt` has 4 matches for the text "Europe", so the output shows `travel_guides/berlitz2/Barcelona-WhatToDo.txt:4`.

**Example 2:**

Command: `grep -c "Great Wall of China" travel_guides/berlitz2/China-WhereToGo.txt`

Output: 
```
1
```

Explanation: The command `grep -c "Great Wall of China" travel_guides/berlitz2/China-WhereToGo.txt` searches for the text "Great Wall of China" in the file `travel_guides/berlitz2/China-WhereToGo.txt`. The `-c` flag counts the number of matches and only shows the number of matches in the file without the actual matches within the file (which would have showed up without the `-c` flag). The file `travel_guides/berlitz2/China-WhereToGo.txt` has 1 match for the text "Great Wall of China", so the output shows `1`.

***

### Command Line Option 2: `grep -v`

The -v flag is used to invert the match. This is useful when you want to see all lines that do not match a certain pattern.

**Example 1:** 

Command: `grep "the" -v travel_guides/berlitz2/Canada-History.txt`

Output: 
```




A Brief HISTORY
New France
The British Take Over
Confederation
The Twentieth Century
Canada’s national unity remains a dynamic “work in progress.” 
THE EARLIEST PEOPLES
The Pioneers
The Inuit
The Kwakiutl
The Dene National
The Blackfoot
The Micmac
Modern Realities




```

Explanation: The command `grep "the" -v travel_guides/berlitz2/Canada-History.txt` searches for the text "the" in the file `travel_guides/berlitz2/Canada-History.txt`. The `-v` flag inverts the match, so it shows all lines that do not match the text "the". For example, the line `The British Take Over` does not match the text "the", so it is shown in the output. The output includes both blank lines and lines that contain the word "The", which may have been unexpected behavior for the user, but is not a bug. 

**Example 2:**

Command: `grep "the" -v -c **/*.txt`

Output: 
``` 
non-fiction/OUP/Abernathy/ch1.txt:13
non-fiction/OUP/Abernathy/ch14.txt:21
non-fiction/OUP/Abernathy/ch15.txt:16
non-fiction/OUP/Abernathy/ch2.txt:14
non-fiction/OUP/Abernathy/ch3.txt:18
non-fiction/OUP/Abernathy/ch6.txt:23
non-fiction/OUP/Abernathy/ch7.txt:14
non-fiction/OUP/Abernathy/ch8.txt:13
non-fiction/OUP/Abernathy/ch9.txt:13
non-fiction/OUP/Berk/CH4.txt:124
non-fiction/OUP/Berk/ch1.txt:68
non-fiction/OUP/Berk/ch2.txt:65
non-fiction/OUP/Berk/ch7.txt:79
non-fiction/OUP/Castro/chA.txt:91
non-fiction/OUP/Castro/chB.txt:109
non-fiction/OUP/Castro/chC.txt:29
non-fiction/OUP/Castro/chL.txt:27
non-fiction/OUP/Castro/chM.txt:80
non-fiction/OUP/Castro/chN.txt:44
non-fiction/OUP/Castro/chO.txt:37
... and more, but you get the idea
```

Explanation: The command `grep "the" -v -c **/*.txt` searches for the text "the" in all text files in the current directory and all subdirectories, as specified by the globstar and the *.txt patterns, respectively. The `-v` flag inverts the match, so it shows all lines that do not match the text "the". The `-c` flag counts the number of matches and only shows the number of (inverted) matches in each file without the actual (inverted) matches within the files (which would have showed up without the `-c` flag). For example, the file `non-fiction/OUP/Berk/CH4.txt` has 124 (inverted) matches for the text "the", so the output shows `non-fiction/OUP/Berk/CH4.txt:124`. I used the `-c` flag here to make the output more readable by outputting the number of lines in each file and not the actual text itself, but it is not necessary for the `-v` command to work.

***

### Command Line Option 3: `grep -i`

The -i flag is used to ignore case. This is useful when you want to search for a pattern that is case insensitive.

**Example 1:** 

Command: `grep -i -c "after" travel_guides/berlitz2/Canada-History.txt`

Output: 
```
16
```

Explanation: The command `grep -i -c "after" travel_guides/berlitz2/Canada-History.txt` searches for the text "after" in the file `travel_guides/berlitz2/Canada-History.txt`. The `-i` flag ignores case, so it matches both "after" and "After" (as well as other variations like "AFTER" and "AfTeR"). The `-c` flag counts the number of matches and only shows the number of matches in the file without the actual matches within the file (which would have showed up without the `-c` flag). The file `travel_guides/berlitz2/Canada-History.txt` has 16 matches for the case-insensitive pattern "after", so the output shows `16`. For context, there are only 9 matches of case-sensitive "after" in the file. The command would have worked without the `-c` flag, but was used here to make the output more readable by outputting the number of lines in each file and not the actual text itself.

**Example 2:**

Command: `grep "Europe" -i -c travel_guides/berlitz2/**/*.txt`

Output: 
```
travel_guides/berlitz2/Algarve-History.txt:5
travel_guides/berlitz2/Algarve-Intro.txt:4
travel_guides/berlitz2/Algarve-WhatToDo.txt:3
travel_guides/berlitz2/Algarve-WhereToGo.txt:8
travel_guides/berlitz2/Amsterdam-History.txt:7
travel_guides/berlitz2/Amsterdam-Intro.txt:3
travel_guides/berlitz2/Amsterdam-WhatToDo.txt:3
travel_guides/berlitz2/Amsterdam-WhereToGo.txt:4
travel_guides/berlitz2/Athens-History.txt:4
travel_guides/berlitz2/Athens-Intro.txt:2
travel_guides/berlitz2/Athens-WhatToDo.txt:4
travel_guides/berlitz2/Athens-WhereToGo.txt:5
travel_guides/berlitz2/Bahamas-History.txt:3
travel_guides/berlitz2/Bahamas-Intro.txt:0
travel_guides/berlitz2/Bahamas-WhatToDo.txt:1
travel_guides/berlitz2/Bahamas-WhereToGo.txt:1
travel_guides/berlitz2/Bali-History.txt:1
travel_guides/berlitz2/Bali-WhatToDo.txt:0
travel_guides/berlitz2/Bali-WhereToGo.txt:4
travel_guides/berlitz2/Barcelona-History.txt:7
travel_guides/berlitz2/Barcelona-WhatToDo.txt:4
travel_guides/berlitz2/Barcelona-WhereToGo.txt:3
travel_guides/berlitz2/Beijing-History.txt:3
travel_guides/berlitz2/Beijing-WhatToDo.txt:1
travel_guides/berlitz2/Beijing-WhereToGo.txt:3
travel_guides/berlitz2/Berlin-History.txt:6
travel_guides/berlitz2/Berlin-WhatToDo.txt:2
travel_guides/berlitz2/Berlin-WhereToGo.txt:13
travel_guides/berlitz2/Bermuda-WhatToDo.txt:1
travel_guides/berlitz2/Bermuda-WhereToGo.txt:1
travel_guides/berlitz2/Bermuda-history.txt:1
travel_guides/berlitz2/Boston-WhereToGo.txt:4
travel_guides/berlitz2/Budapest-History.txt:5
travel_guides/berlitz2/Budapest-WhatToDo.txt:4
travel_guides/berlitz2/Budapest-WhereoGo.txt:9
travel_guides/berlitz2/California-History.txt:3
... and more, but you get the idea
```

Explanation: The command `grep "Europe" -i -c travel_guides/berlitz2/**/*.txt` searches for the text "Europe" in all text files in the directory `travel_guides/berlitz2` and all subdirectories, as specified by the globstar and the *.txt patterns, respectively. The `-i` flag ignores case, so it matches both "Europe" and "europe" (as well as other variations like "EUROPE" and "EuRoPe"). The `-c` flag counts the number of matches and only shows the number of matches in each file without the actual matches within the files (which would have showed up without the `-c` flag). For example, the file `travel_guides/berlitz2/Algarve-History.txt` has 5 matches for the case-insensitive pattern "Europe", so the output shows `travel_guides/berlitz2/Algarve-History.txt:5`. I used the `-c` flag here to make the output more readable by outputting the number of lines in each file and not the actual text itself, but it is not necessary for the `-i` command to work.

***

### Command Line Option 4: `grep -n`

The -n flag is used to print the line number of each matching line. This is useful when you want to know the line number of each matching line.

**Example 1:** 

Command: `grep -n "After" travel_guides/berlitz2/Canada-History.txt`

Output: 
```
6:I s it history or blarney to suggest that St. Brendan, a sixth-century monk from Galway, was the first European to reach Canada? The good people of Newfoundland, where he is said to have landed, like to think he was. After all, on his return he told of being attacked by insects as big as chickens. “Of course,” say the Newfies, “they must have been our giant mosquitoes!”
13:After winters on the Bay of Fundy had proved too harsh, Samuel de Champlain and his first batch of French settlers left Nova Scotia and moved over to the St. Lawrence River in 1608. Within ten years, both tenant farmers (habitants) and fur traders (coureurs de bois, literally wood-runners) were colonizing Québec — New France — at the point where the river narrows.
19:The French army burned its flags and sailed home, followed by most of the merchants and colonial leaders, leaving the habitants to fend for themselves. After 150 years of courageous struggle against the harsh Canadian wilderness, New France was abandoned, the old country displaying a cruel lack of enthusiasm for what Voltaire dismissed as quelques arpens de neige — “a few acres of snow.” 
24:The land west of Ontario was written off as one big empty wilderness until Alexander Mackenzie completed the first transcontinental crossing, and Simon Fraser and David Thompson mapped out the rivers and mountains of British Columbia and the Rockies. The Hudson’s Bay Company fought for control of the fur trade with the North West Company, which formed in 1783. The Nor’westers commandeered the French system of forts, depots, and canoe brigades; they inter-married with native peoples and produced new clans of so-called Métis. After years of fierce armed struggle for trading posts around Hudson Bay and lakes Winnipeg and Superior, the Nor’westers threw in their lot with the H.B.C., bringing a wilder, more imaginative spirit to the staid old company.
... and more, but you get the idea
```

Explanation: The command `grep -n "After" travel_guides/berlitz2/Canada-History.txt` searches for the text "After" in the file `travel_guides/berlitz2/Canada-History.txt` and prints the line number of each matching line. For example, the line `13:After winters on the Bay of Fundy had proved too harsh, Samuel de Champlain...` has the word "After" on line 13, so the output shows `13:After winters on the Bay of Fundy had proved too harsh, Samuel de Champlain...`

**Example 2:**

Command: `grep -n "After" travel_guides/berlitz2/**/*.txt`

Output: 
```
travel_guides/berlitz2/Algarve-History.txt:11:The long struggle by Christians to expel the Moors (a campaign known as the Reconquista, or Reconquest) began towards the end of the eighth century a.d. By the 11th century, Portucale consisted of a small section of Castile and León (today’s northern Portugal). Yet it wasn’t until the 12th century that significant gains were made to take back southern Iberia. The beginning of the end came in the Battle of Ourique in 1139. After the victory, Count Afonso Henriques proclaimed himself the first king of Portugal, making it one of the first nation-states in Europe.
travel_guides/berlitz2/Algarve-History.txt:39:The sudden end of more than seven centuries of monarchy brought confusion and crisis to the country. Presidents and prime ministers were ushered into and out of office an unbelievable 45 times between 1910 and 1926, until a military revolution suspended Portugal’s problematic democracy. After six years of power, General Oscar Carmona appointed his finance minister, António de Oliveira Salazar, to be Prime Minister, a position he was to hold until 1968. Salazar’s repressive rule and austerity measures rid the Portuguese economy of debt, though poverty increased. Portugal remained neutral during World War II, and Salazar demonstrated his financial acumen by selling materials and supplies to both sides.
travel_guides/berlitz2/Algarve-WhereToGo.txt:127:After the salty flavor of Olhão and the rural serenity of Moncarapacho, the aristocratic bearings of Tavira, one of the true gems of the Algarve, may come as something of a surprise. One of the region’s most historic cities, its Moorish, Reconquista, and Renaissance roots are clearly visible.
travel_guides/berlitz2/Algarve-WhereToGo.txt:137:The Guadiana River, which runs into the Atlantic 3 km (2 miles) east of Monte Gordo, served as a natural frontier for 2,000 years, forming the boundary between the Roman provinces of Lusitania (Portugal) and Baetica (southern Spain). This explains the strategic importance of Castro Marim, a former fortress town rising from the flatlands to command the broad river. For five centuries its primitive castle-fortress was occupied by the Moors. After the Reconquest it became the home of the new Military Order of Christ (succeeding the disbanded Knights Templars). Look for the inscription inside the main entrance proclaiming that Prince Henry the Navigator, who was a governor of the order, once lived here. These days the castle itself is in need of defense and restoration, and although it may no longer be of any military value, its broad, unpolluted marshlands do attract large numbers of wading birds. The area is protected by the National Parks service and is very popular with birdwatchers.
travel_guides/berlitz2/Amsterdam-WhereToGo.txt:30:After pausing to take a photograph, cross the street to Jodenbreestraat (Jewish Broad Street) and the 3-story brick building with red shutters. This is Museum Het Rembrandthuis (Rembrandt’s House), and was home to the great artist from 1639 to1660.
... and more, but you get the idea
```

Explanation: The command `grep -n "After" travel_guides/berlitz2/**/*.txt` searches for the text "After" in all text files in the directory `travel_guides/berlitz2/` and all subdirectories and prints the line number of each matching line. For example, the line `travel_guides/berlitz2/Algarve-History.txt:11:The long struggle by Christians to expel the Moors (a campaign known as the...After...making it one of the first nation-states in Europe.` has the word "After", so it is outputted.