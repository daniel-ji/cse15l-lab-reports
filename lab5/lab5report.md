# CSE 15L, LAB 5

### Daniel Ji, March 9, 2023

## Chosen command: `find`

### Source for all options: https://www.geeksforgeeks.org/grep-command-in-unixlinux/

Note: Before running these commands, globstar was enabled, which is why the `**` is used in the commands. Globstar is a bash option that allows for recursive globbing. For example, `**/*.java` will match all files with the `.java` extension in the current directory and all subdirectories. It was enabled with the command `shopt -s globstar`.

Note: The current working directory is the written_2 folder of skill demo 1. 

***

### Command Line Option 1: `find -name`

The `-name` option allows for the user to search for files with a specific name. The command `find . -name History*` will search for all files with the pattern `History*` in the current directory and all subdirectories. The output of this command is as follows:

Command: `find . -name History*`

Output: 
```bash
./travel_guides/berlitz1/HistoryIndia.txt
./travel_guides/berlitz1/HistoryIstanbul.txt
./travel_guides/berlitz1/HistoryHongKong.txt
./travel_guides/berlitz1/HistoryIbiza.txt
./travel_guides/berlitz1/HistoryEgypt.txt
./travel_guides/berlitz1/HistoryMallorca.txt
./travel_guides/berlitz1/HistoryEdinburgh.txt
./travel_guides/berlitz1/HistoryFWI.txt
./travel_guides/berlitz1/HistoryDublin.txt
./travel_guides/berlitz1/HistoryItaly.txt
./travel_guides/berlitz1/HistoryIsrael.txt
./travel_guides/berlitz1/HistoryJapan.txt
./travel_guides/berlitz1/HistoryFrance.txt
./travel_guides/berlitz1/HistoryMadeira.txt
./travel_guides/berlitz1/HistoryJamaica.txt
./travel_guides/berlitz1/HistoryGreek.txt
./travel_guides/berlitz1/HistoryLasVegas.txt
./travel_guides/berlitz1/HistoryMalaysia.txt
./travel_guides/berlitz1/HistoryLakeDistrict.txt
./travel_guides/berlitz1/HistoryJerusalem.txt
./travel_guides/berlitz1/HistoryHawaii.txt
./travel_guides/berlitz1/HistoryMadrid.txt
```

Additional example: 
Description: The command `find . -name HandRLosAngeles.txt` will search for all files with the name `HandRLosAngeles.txt` in the current directory and all subdirectories. The output of this command is as follows:

Command: `find . -name HandRLosAngeles.txt`

Output:
```bash
./travel_guides/berlitz1/HandRLosAngeles.txt
```

### Command Line Option 2: `find -type`

The `-type` option allows for the user to search for files of a specific type. The command `find . -type f` will search for all files in the current directory and all subdirectories, as opposed to files and directories. The output of this command is as follows:

Command: `find ./non-fiction -type f`

Output: 
```bash
./non-fiction/OUP/Rybczynski/ch1.txt
./non-fiction/OUP/Rybczynski/ch3.txt
./non-fiction/OUP/Rybczynski/ch2.txt
./non-fiction/OUP/Castro/chC.txt
./non-fiction/OUP/Castro/chN.txt
./non-fiction/OUP/Castro/chA.txt
./non-fiction/OUP/Castro/chQ.txt
./non-fiction/OUP/Castro/chR.txt
./non-fiction/OUP/Castro/chB.txt
./non-fiction/OUP/Castro/chZ.txt
./non-fiction/OUP/Castro/chP.txt
./non-fiction/OUP/Castro/chV.txt
./non-fiction/OUP/Castro/chY.txt
./non-fiction/OUP/Castro/chL.txt
./non-fiction/OUP/Castro/chO.txt
./non-fiction/OUP/Castro/chW.txt
./non-fiction/OUP/Castro/chM.txt
./non-fiction/OUP/Berk/CH4.txt
./non-fiction/OUP/Berk/ch1.txt
./non-fiction/OUP/Berk/ch2.txt
./non-fiction/OUP/Berk/ch7.txt
./non-fiction/OUP/Kauffman/ch5.txt
./non-fiction/OUP/Kauffman/ch6.txt
./non-fiction/OUP/Kauffman/ch8.txt
./non-fiction/OUP/Kauffman/ch9.txt
./non-fiction/OUP/Kauffman/ch4.txt
./non-fiction/OUP/Kauffman/ch1.txt
./non-fiction/OUP/Kauffman/ch3.txt
./non-fiction/OUP/Kauffman/ch10.txt
./non-fiction/OUP/Kauffman/ch7.txt
./non-fiction/OUP/Fletcher/ch5.txt
./non-fiction/OUP/Fletcher/ch6.txt
./non-fiction/OUP/Fletcher/ch9.txt
./non-fiction/OUP/Fletcher/ch1.txt
./non-fiction/OUP/Fletcher/ch2.txt
./non-fiction/OUP/Fletcher/ch10.txt
./non-fiction/OUP/Abernathy/ch6.txt
./non-fiction/OUP/Abernathy/ch8.txt
./non-fiction/OUP/Abernathy/ch9.txt
./non-fiction/OUP/Abernathy/ch1.txt
./non-fiction/OUP/Abernathy/ch3.txt
./non-fiction/OUP/Abernathy/ch15.txt
./non-fiction/OUP/Abernathy/ch2.txt
./non-fiction/OUP/Abernathy/ch14.txt
./non-fiction/OUP/Abernathy/ch7.txt
```

Additional example:
Description: The command `find . -type d` will search for all directories in the current directory and all subdirectories.

Command: `find . -type d`

Output:
```bash
.
./non-fiction
./non-fiction/OUP
./non-fiction/OUP/Rybczynski
./non-fiction/OUP/Castro
./non-fiction/OUP/Berk
./non-fiction/OUP/Kauffman
./non-fiction/OUP/Fletcher
./non-fiction/OUP/Abernathy
./travel_guides
./travel_guides/berlitz2
./travel_guides/berlitz1
```

### Command Line Option 3: `find -size`

The `-size` option allows for the user to search for files of a specific size. The command `find . -size +100k` will search for all files in the current directory and all subdirectories that are larger than 100 kilobytes. The output of this command is as follows:

Command: `find . -size +100k`

Output:
```bash
./non-fiction/OUP/Berk/CH4.txt
./non-fiction/OUP/Berk/ch2.txt
./travel_guides/berlitz2/China-WhereToGo.txt
./travel_guides/berlitz2/Canada-WhereToGo.txt
./travel_guides/berlitz2/Portugal-WhereToGo.txt
./travel_guides/berlitz1/WhereToFrance.txt
./travel_guides/berlitz1/WhereToMalaysia.txt
./travel_guides/berlitz1/WhereToItaly.txt
./travel_guides/berlitz1/WhereToJapan.txt
./travel_guides/berlitz1/WhereToIndia.txt
```

Additional example:
Description: The command `find ./non-fiction -size -100k` will search for all files in the non-fiction directory and all subdirectories that are smaller than 100 kilobytes.

Command: `find ./non-fiction -size -100k`

Output: 
```bash
./non-fiction
./non-fiction/OUP
./non-fiction/OUP/Rybczynski
./non-fiction/OUP/Rybczynski/ch1.txt
./non-fiction/OUP/Rybczynski/ch3.txt
./non-fiction/OUP/Rybczynski/ch2.txt
./non-fiction/OUP/Castro
./non-fiction/OUP/Castro/chC.txt
./non-fiction/OUP/Castro/chN.txt
./non-fiction/OUP/Castro/chA.txt
./non-fiction/OUP/Castro/chQ.txt
./non-fiction/OUP/Castro/chR.txt
./non-fiction/OUP/Castro/chB.txt
./non-fiction/OUP/Castro/chZ.txt
./non-fiction/OUP/Castro/chP.txt
./non-fiction/OUP/Castro/chV.txt
./non-fiction/OUP/Castro/chY.txt
./non-fiction/OUP/Castro/chL.txt
./non-fiction/OUP/Castro/chO.txt
./non-fiction/OUP/Castro/chW.txt
./non-fiction/OUP/Castro/chM.txt
./non-fiction/OUP/Berk
./non-fiction/OUP/Berk/ch1.txt
./non-fiction/OUP/Berk/ch7.txt
./non-fiction/OUP/Kauffman
./non-fiction/OUP/Kauffman/ch5.txt
./non-fiction/OUP/Kauffman/ch6.txt
./non-fiction/OUP/Kauffman/ch8.txt
./non-fiction/OUP/Kauffman/ch9.txt
./non-fiction/OUP/Kauffman/ch4.txt
./non-fiction/OUP/Kauffman/ch1.txt
./non-fiction/OUP/Kauffman/ch3.txt
./non-fiction/OUP/Kauffman/ch10.txt
./non-fiction/OUP/Kauffman/ch7.txt
./non-fiction/OUP/Fletcher
./non-fiction/OUP/Fletcher/ch5.txt
./non-fiction/OUP/Fletcher/ch6.txt
./non-fiction/OUP/Fletcher/ch9.txt
./non-fiction/OUP/Fletcher/ch1.txt
./non-fiction/OUP/Fletcher/ch2.txt
./non-fiction/OUP/Fletcher/ch10.txt
./non-fiction/OUP/Abernathy
./non-fiction/OUP/Abernathy/ch6.txt
./non-fiction/OUP/Abernathy/ch8.txt
./non-fiction/OUP/Abernathy/ch9.txt
./non-fiction/OUP/Abernathy/ch1.txt
./non-fiction/OUP/Abernathy/ch3.txt
./non-fiction/OUP/Abernathy/ch15.txt
./non-fiction/OUP/Abernathy/ch2.txt
./non-fiction/OUP/Abernathy/ch14.txt
./non-fiction/OUP/Abernathy/ch7.txt
```

Command line option 4: `find -empty`

The `-empty` option allows for the user to search for empty files. The command `find . -empty` will search for all empty files in the current directory and all subdirectories. After creating some empty files, the output of this command is as follows:

Preliminary commands: 
```
touch non-fiction/empty.txt
touch non-fiction/OUP/Fletcher/empty.txt
touch travel_guides/berlitz1/empty.txt
touch non-fiction/OUP/Fletcher/secret.txt
touch travel_guides/berlitz1/text.txt
```

Command: `find . -empty`

Output:
```bash
./non-fiction/OUP/Fletcher/empty.txt
./non-fiction/OUP/Fletcher/secret.txt
./non-fiction/empty.txt
./travel_guides/berlitz1/text.txt
./travel_guides/berlitz1/empty.txt
```

Additional example:
Description: The command `find . -empty -name "empty.txt"` will search for all empty files in the current directory and all subdirectories that have the name "empty.txt".

Command: `find . -empty -name "empty.txt"`

Output:
```bash
./non-fiction/OUP/Fletcher/empty.txt
./non-fiction/empty.txt
./travel_guides/berlitz1/empty.txt
```

## For Fun Chosen Command: `tar`

### Compressing Archives

The `tar` command is used to create and extract tar archives. The command `tar -czvf archive.tar.gz non-fiction` will create a tar archive named archive.tar.gz that contains the non-fiction directory. The -c option creates a new archive, the -z option compresses the archive with gzip, the -v option displays verbose output, and the -f option specifies the name of the archive.
The output of this command is as follows:

Command: `tar -czvf archive.tar.gz non-fiction`

Output:
```bash
non-fiction/
non-fiction/OUP/
non-fiction/OUP/Rybczynski/
non-fiction/OUP/Rybczynski/ch1.txt
non-fiction/OUP/Rybczynski/ch3.txt
non-fiction/OUP/Rybczynski/ch2.txt
non-fiction/OUP/Castro/
non-fiction/OUP/Castro/chC.txt
non-fiction/OUP/Castro/chN.txt
non-fiction/OUP/Castro/chA.txt
non-fiction/OUP/Castro/chQ.txt
non-fiction/OUP/Castro/chR.txt
non-fiction/OUP/Castro/chB.txt
non-fiction/OUP/Castro/chZ.txt
non-fiction/OUP/Castro/chP.txt
non-fiction/OUP/Castro/chV.txt
non-fiction/OUP/Castro/chY.txt
non-fiction/OUP/Castro/chL.txt
non-fiction/OUP/Castro/chO.txt
non-fiction/OUP/Castro/chW.txt
non-fiction/OUP/Castro/chM.txt
non-fiction/OUP/Berk/
non-fiction/OUP/Berk/CH4.txt
non-fiction/OUP/Berk/ch1.txt
non-fiction/OUP/Berk/ch2.txt
non-fiction/OUP/Berk/ch7.txt
non-fiction/OUP/Kauffman/
non-fiction/OUP/Kauffman/ch5.txt
non-fiction/OUP/Kauffman/ch6.txt
non-fiction/OUP/Kauffman/ch8.txt
non-fiction/OUP/Kauffman/ch9.txt
non-fiction/OUP/Kauffman/ch4.txt
non-fiction/OUP/Kauffman/ch1.txt
non-fiction/OUP/Kauffman/ch3.txt
non-fiction/OUP/Kauffman/ch10.txt
non-fiction/OUP/Kauffman/ch7.txt
non-fiction/OUP/Fletcher/
non-fiction/OUP/Fletcher/ch5.txt
non-fiction/OUP/Fletcher/ch6.txt
non-fiction/OUP/Fletcher/ch9.txt
non-fiction/OUP/Fletcher/ch1.txt
non-fiction/OUP/Fletcher/ch2.txt
non-fiction/OUP/Fletcher/empty.txt
non-fiction/OUP/Fletcher/ch10.txt
non-fiction/OUP/Fletcher/secret.txt
non-fiction/OUP/Abernathy/
non-fiction/OUP/Abernathy/ch6.txt
non-fiction/OUP/Abernathy/ch8.txt
non-fiction/OUP/Abernathy/ch9.txt
non-fiction/OUP/Abernathy/ch1.txt
non-fiction/OUP/Abernathy/ch3.txt
non-fiction/OUP/Abernathy/ch15.txt
non-fiction/OUP/Abernathy/ch2.txt
non-fiction/OUP/Abernathy/ch14.txt
non-fiction/OUP/Abernathy/ch7.txt
non-fiction/empty.txt
```

Directory contents:

Command: `ls -l --block-size=M`

```
total 1M
-rw-r--r-- 1 daniel daniel 1M Mar  9 17:37 archive.tar.gz
drwxr-xr-x 3 daniel daniel 1M Mar  9 17:30 non-fiction
drwxr-xr-x 4 daniel daniel 1M Feb  4 19:47 travel_guides
```

### Extracting Archives

The command `tar -xzvf archive.tar.gz` will extract the contents of the archive.tar.gz file into the current directory. The -x option extracts the contents of the archive, the -z option decompresses the archive with gzip, the -v option displays verbose output, and the -f option specifies the name of the archive. The output of this command is as follows:

Preliminary commands:
```
rm -rf non-fiction
```

Command: `tar -xzvf archive.tar.gz`

Output:
```bash
non-fiction/
non-fiction/OUP/
non-fiction/OUP/Rybczynski/
non-fiction/OUP/Rybczynski/ch1.txt
non-fiction/OUP/Rybczynski/ch3.txt
non-fiction/OUP/Rybczynski/ch2.txt
non-fiction/OUP/Castro/
non-fiction/OUP/Castro/chC.txt
non-fiction/OUP/Castro/chN.txt
non-fiction/OUP/Castro/chA.txt
non-fiction/OUP/Castro/chQ.txt
non-fiction/OUP/Castro/chR.txt
non-fiction/OUP/Castro/chB.txt
non-fiction/OUP/Castro/chZ.txt
non-fiction/OUP/Castro/chP.txt
non-fiction/OUP/Castro/chV.txt
non-fiction/OUP/Castro/chY.txt
non-fiction/OUP/Castro/chL.txt
non-fiction/OUP/Castro/chO.txt
non-fiction/OUP/Castro/chW.txt
non-fiction/OUP/Castro/chM.txt
non-fiction/OUP/Berk/
non-fiction/OUP/Berk/CH4.txt
non-fiction/OUP/Berk/ch1.txt
non-fiction/OUP/Berk/ch2.txt
non-fiction/OUP/Berk/ch7.txt
non-fiction/OUP/Kauffman/
non-fiction/OUP/Kauffman/ch5.txt
non-fiction/OUP/Kauffman/ch6.txt
non-fiction/OUP/Kauffman/ch8.txt
non-fiction/OUP/Kauffman/ch9.txt
non-fiction/OUP/Kauffman/ch4.txt
non-fiction/OUP/Kauffman/ch1.txt
non-fiction/OUP/Kauffman/ch3.txt
non-fiction/OUP/Kauffman/ch10.txt
non-fiction/OUP/Kauffman/ch7.txt
non-fiction/OUP/Fletcher/
non-fiction/OUP/Fletcher/ch5.txt
non-fiction/OUP/Fletcher/ch6.txt
non-fiction/OUP/Fletcher/ch9.txt
non-fiction/OUP/Fletcher/ch1.txt
non-fiction/OUP/Fletcher/ch2.txt
non-fiction/OUP/Fletcher/empty.txt
non-fiction/OUP/Fletcher/ch10.txt
non-fiction/OUP/Fletcher/secret.txt
non-fiction/OUP/Abernathy/
non-fiction/OUP/Abernathy/ch6.txt
non-fiction/OUP/Abernathy/ch8.txt
non-fiction/OUP/Abernathy/ch9.txt
non-fiction/OUP/Abernathy/ch1.txt
non-fiction/OUP/Abernathy/ch3.txt
non-fiction/OUP/Abernathy/ch15.txt
non-fiction/OUP/Abernathy/ch2.txt
non-fiction/OUP/Abernathy/ch14.txt
non-fiction/OUP/Abernathy/ch7.txt
non-fiction/empty.txt
```

Directory contents:

Command: `ls -l --block-size=M`

```
total 1M
-rw-r--r-- 1 daniel daniel 1M Mar  9 17:37 archive.tar.gz
-rw-r--r-- 1 daniel daniel 1M Mar  9 17:39 labreport5.md
drwxr-xr-x 3 daniel daniel 1M Mar  9 17:30 non-fiction
drwxr-xr-x 4 daniel daniel 1M Feb  4 19:47 travel_guides
```
