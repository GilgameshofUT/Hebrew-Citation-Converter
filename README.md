# Hebrew-Citation-Converter

A simple python script to convert Book, Chapter, and Verse citations from the Hebrew Bible, to their equivalent citations for most English Bibles.

The division of Biblical texts into numbered chapters and verses was a brilliant post Biblical innovation started primarily by Christians, but readily adopted by Jews. It allowed precise and easy references to exact parts of the text. Unfortunately, while both Christians and Jews adopted the system and they are quite close most of the time, there are differences in implementation. This amounts to about 2,000 verses that have a slightly different chapter or verse number between the 2 systems. In a book of over 23,000 verses that isn't a lot, but it is enough to cause some confusion.

Almost all Hebrew Bibles today follow the same verse numbering systems as do major Jewish English Translations such as the translations from JPS (both 1917 and 1985\) and the translations from Koren, Artscroll and others. KJV, ESV, NIV and many others follow the typical English numbering system. Strong's Concordance published back in the 19th Century had a nice one pager listing all the differences in the two systems. [https://archive.org/details/exhaustiveconcor1890stro/page/127/mode/1up](https://archive.org/details/exhaustiveconcor1890stro/page/127/mode/1up)  I could not find that anyone had made this information available online in any more updated format, which was odd. I was also surprised no one had undertaken to make a simple conversion script that I could find. So I made my own. It is not much more than a straightforward verse to verse mapping from the Hebrew citation to the English. I attempted to support verse ranges but was unable to get the logic of adjusting chapter numbers to correctly work. Perhaps someone might like to undertake that.

The script has no dependencies. Just run it:

```
python hebrew-english-verse-convert.py
```

Some background on this. The most differences are to be found in the Psalms, where they are often introduced with a superscription, “A Psalm of David” or similar phrase. Jewish editors numbered this introduction as verse 1, Christians didn’t number it at all leaving it as a sort of verse 0\. As texts became digital most people didn’t like referencing Ps 22:0 so the English texts generally folded the superscriptions into verse 1\. The means Ps 22:1 (Hebrew) \-\> Ps 22:1 (English) but also Ps 22:2 (Hebrew) \-\> Ps 22:1 (English) and Ps 22:3 (Hebrew) \-\> Ps 22:2 (English) and so on for the rest of the chapter. Of course this isn’t entirely consistent throughout either system. Since there really isn’t a verse 0 in modern digital copies I was able to ignore many lines from Strong’s chart and just leave verse 1 mapping to verse 1\.   

The Psalms are not the only problem spot though. Sometimes for specific religious reasons a verse was moved such as moving Isaiah 8:23, last verse in that chapter, to be the first verse of 9:1 because it mentions Galilee and is used in the New Testament (before there were chapters and verses) with the verse that follows. Other differences are more arbitrary and the reason for them is lost to time (as far as I know). Why does Joel have 4 chapters in Hebrew but 3 chapters in English? ¯\\\_(ツ)\_/¯ But it is nicely balanced by Malachi having 4 chapters in English and only 3 in Hebrew. There are of course a few oddities as well where verse divisions are split differently between the systems, but this is pretty rare.

At any rate I cleaned up the chart from Strong’s quite a bit and after several attempts to be clever I finally decided a brute force of verse to verse mapping was the best solution. I had AI expand it out for me and I think it did it correctly. If there are errors or missing needed mappings feel free to let me know. For my own purposes this is part of a larger program where I am working on both Hebrew Biblical text and several English translations, so I needed a way to easily align them. My citations are primarily to the Hebrew system so this is used to grab the correct translation verse from the English. With a minor amount of work it could be reversed to go the other direction.


| Hebrew          | English         |
| --------------- | --------------- |
| Gen 32:1        | Gen 31:55       |
| Gen 32:2-33     | Gen 32:1-32     |
| Ex 7:26-29      | Ex 8:1-4        |
| Ex 8:1-28       | Ex 8:5-32       |
| Ex 21:37        | Ex 22:1         |
| Ex 22:1-30      | Ex 22:2-31      |
| Lev 5:20-26     | Lev 6:1-7       |
| Lev 6:1-23      | Lev 6:8-30      |
| Num 17: 1-15    | Num 16:36-50    |
| Num 17:16-28    | Num 17:1-13     |
| Num 30:1        | Num 29:40       |
| Num 30:2-17     | Num 30:1-16     |
| Deut 5:17-30    | Deut 5:18-33    |
| Deut 13:1       | Deut 12:32      |
| Deut 13:2-19    | Deut 13:1-18    |
| Deut 23:1       | Deut 22:30      |
| Deut 23:2-26    | Deut 23:1-25    |
| Deut 28:69      | Deut 29:1       |
| Deut 29:1-28    | Deut 29:2-29    |
| 1Sam 21:1       | 1Sam 20:42      |
| 1Sam 21:2-16    | 1Sam 21:1-15    |
| 1Sam 24:1       | 1Sam 23:29      |
| 1Sam 24:2-23    | 1Sam 24:1-22    |
| 2Sam 19:1       | 2Sam 18:33      |
| 2Sam 19:2-44    | 2Sam 19:1-43    |
| 1Kings 5:1-14   | 1Kings 4:21-34  |
| 1Kings 5:15-32  | 1Kings 5:1-18   |
| 1Kings 22:44    | 1Kings 22:43    |
| 1Kings 22:45-54 | 1Kings 22:44-53 |
| 2Kings 12:1     | 2Kings 11:21    |
| 2Kings 12:2-22  | 2Kings 12:1-21  |
| 1Chr 5:27-41    | 1Chr 6:1-15     |
| 1Chr 6:1-66     | 1Chr 6:16-81    |
| 2Chr 1:18       | 2Chr 2:1        |
| 2Chr 2:1-17     | 2Chr 2:2-18     |
| 2Chr 13:23      | 2Chr 14:1       |
| 2Chr 14:1-14    | 2Chr 14:2-15    |
| Neh 3:33-38     | Neh 4:1-6       |
| Neh 4:1-17      | Neh 4:7-23      |
| Neh 10:1        | Neh 9:38        |
| Neh 10:2-40     | Neh 10:1-39     |
| Job 40:25-32    | Job 41:1-8      |
| Job 41:1-26     | Job 41:9-34     |
| Ps 3:2-9        | Ps 3:1-8        |
| Ps 4:2-9        | Ps 4:1-8        |
| Ps 5:2-13       | Ps 5:1-12       |
| Ps 6:2-11       | Ps 6:1-10       |
| Ps 7:2-18       | Ps 7:1-17       |
| Ps 8:2-10       | Ps 8:1-9        |
| Ps 9:2-21       | Ps 9:1-20       |
| Ps 12:2-9       | Ps 12:1-8       |
| Ps 13:2-6       | Ps 13:1-5       |
| Ps 18:2-51      | Ps 18:1-50      |
| Ps 19:2-15      | Ps 19:1-14      |
| Ps 20:2-10      | Ps 20:1-9       |
| Ps 21:2-14      | Ps 21:1-13      |
| Ps 22:2-32      | Ps 22:1-31      |
| Ps 30:2-13      | Ps 30:1-12      |
| Ps 31:2-25      | Ps 31:1-24      |
| Ps 34:2-23      | Ps 34:1-22      |
| Ps 36:2-13      | Ps 36:1-12      |
| Ps 38:2-23      | Ps 38:1-22      |
| Ps 39:2-14      | Ps 39:1-13      |
| Ps 40:2-18      | Ps 40:1-17      |
| Ps 41:2-14      | Ps 41:1-13      |
| Ps 42:2-12      | Ps 42:1-11      |
| Ps 44:2-27      | Ps 44:1-26      |
| Ps 45:2-18      | Ps 45:1-17      |
| Ps 46:2-12      | Ps 46:1-11      |
| Ps 47:2-10      | Ps 47:1-9       |
| Ps 48:2-15      | Ps 48:1-14      |
| Ps 49:2-21      | Ps 49:1-20      |
| Ps 51:2         | Ps 51:1         |
| Ps 51:3-21      | Ps 51:1-19      |
| Ps 52:2-11      | Ps 52:1-9       |
| Ps 53:2-7       | Ps 53:1-6       |
| Ps 54:2         | Ps 54:1         |
| Ps 54:3-9       | Ps 54:1-7       |
| Ps 55:2-24      | Ps 55:1-23      |
| Ps 56:2-24      | Ps 56:1-23      |
| Ps 57:2-12      | Ps 57:1-11      |
| Ps 58:2-12      | Ps 58:1-11      |
| Ps 59:2-18      | Ps 59:1-17      |
| Ps 60:2         | Ps 60:1         |
| Ps 60:3-14      | Ps 60:1-12      |
| Ps 61:2-9       | Ps 61:1-8       |
| Ps 62:2-13      | Ps 62:1-12      |
| Ps 63:2-12      | Ps 63:1-11      |
| Ps 64:2-11      | Ps 64:1-10      |
| Ps 65:2-14      | Ps 65:1-13      |
| Ps 67:2-8       | Ps 67:1-7       |
| Ps 68:2-36      | Ps 68:1-35      |
| Ps 69:2-37      | Ps 69:1-36      |
| Ps 70:2-6       | Ps 70:1-5       |
| Ps 74:2-11      | Ps 74:1-10      |
| Ps 76:2-13      | Ps 76:1-12      |
| Ps 77:2-21      | Ps 77:1-20      |
| Ps 80:2-20      | Ps 80:1-19      |
| Ps 81:2-17      | Ps 81:1-16      |
| Ps 83:2-19      | Ps 83:1-18      |
| Ps 84:2-13      | Ps 84:1-12      |
| Ps 85:2-14      | Ps 85:1-13      |
| Ps 88:2-19      | Ps 88:1-18      |
| Ps 89:2-53      | Ps 89:1-52      |
| Ps 92:2-16      | Ps 92:1-15      |
| Ps 102:2-29     | Ps 102:1-28     |
| Ps 108:2-14     | Ps 108:1-13     |
| Ps 140:2-14     | Ps 140:1-13     |
| Ps 142:2-7      | Ps 142:1-6      |
| Eccl 4:17       | Eccl 5:1        |
| Eccl 5: 1-19    | Eccl 5:2-20     |
| Song 7:1        | Song 6:13       |
| Song 7:2-14     | Song 7: 1-13    |
| Isa 8:23        | Isa 9:1         |
| Isa 9:1-20      | Isa 9:2-21      |
| Isa 63:19       | Isa 64:1        |
| Isa 64:1-11     | Isa 64:2-12     |
| Jer 8:23        | Jer 9:1         |
| Jer 9:1-25      | Jer 9:2-26      |
| Ezek 21:1-5     | Ezek 20:45-49   |
| Ezek 21:6-37    | Ezek 21:1-32    |
| Dan 3:31-33     | Dan 4:1-3       |
| Dan 4:1-34      | Dan 4:4-37      |
| Dan 6:1         | Dan 5:31        |
| Dan 6:2-29      | Dan 6:1-28      |
| Hos 2:1-2       | Hos 1:10-11     |
| Hos 2:3-25      | Hos 2:1-23      |
| Hos 12:1        | Hos 11:12       |
| Hos 12:2-15     | Hos 12:1-14     |
| Hos 14:1        | Hos 13:16       |
| Hos 14:2-10     | Hos 14:1-9      |
| Joel 3:1-5      | Joel 2:28-32    |
| Joel 4:1-21     | Joel 3:1-21     |
| Jon 2:1         | Jon 1:17        |
| Jon 2:2-11      | Jon 2:1-10      |
| Mic 4:14        | Mic 5:1         |
| Mic 5:1-14      | Mic 5:2-15      |
| Nah 2:1         | Nah 1:15        |
| Nah 2:2-14      | Nah 2:1-13      |
| Zech 2:1-4      | Zech 1:18-21    |
| Zech 2:5-17     | Zech 2:1-13     |
| Mal 3:19-24     | Mal 4:1-6       |
