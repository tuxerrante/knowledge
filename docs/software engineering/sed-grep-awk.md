[https://www.thegeekstuff.com/2009/10/unix-sed-tutorial-advanced-sed-substitution-examples/](https://www.thegeekstuff.com/2009/10/unix-sed-tutorial-advanced-sed-substitution-examples/)

[https://unix.stackexchange.com/questions/32907/what-characters-do-i-need-to-escape-when-using-sed-in-a-sh-script](https://unix.stackexchange.com/questions/32907/what-characters-do-i-need-to-escape-when-using-sed-in-a-sh-script)

[8 Powerful Awk Built-in Variables – FS, OFS, RS, ORS, NR, NF, FILENAME, FNR](https://www.thegeekstuff.com/2010/01/8-powerful-awk-built-in-variables-fs-ofs-rs-ors-nr-nf-filename-fnr/)

**FS** is any single character or regular expression which you want to use as a input field separator.  
**OFS** is an output equivalent of awk FS variable. By default awk OFS is a single space character.  
**RS** defines a line.  
**ORS** is an Output equivalent of RS. Each record in the output will be printed with this delimiter.  
**NR** gives you the total number of records being processed or line number.   
**NF** gives you the total number of fields in a record

Chiude le parole cercate tra parentesi, case insensitive  
sed \-e 's/\\bthy\\b/{&}/gi'

Inverte l’ordine dei gruppi di cifre  
sed 's/\\(\[0-9\]\\{4\\}\\) \\(\[0-9\]\\{4\\} \\)\\(\[0-9\]\\{4\\} \\)\\(\[0-9\]\\{4\\}\\)/\\4 \\3\\2\\1/g'

$ cat awk\_avg.awk   
{  
    avg=($2+$3+$4)/3;  
   
    if (avg \< 50\) grade="FAIL";  
    else if (avg\>=50 && avg\<60) grade="C";  
    else if (avg\>=60 && avg\<80) grade="B";  
    else grade="A";

    print $0,":",grade;  
}  
*OUTPUT*  
*$ awk \-f awk\_avg.awk colonne.txt*   
*A 25 27 50 : FAIL*  
*B 35 37 75 : FAIL*  
*C 75 78 80 : B*  
*D 99 88 76 : A*  
\---

$ cat merge\_lines.awk   
BEGIN { evenLine \= 0; }  
{  
    if ( evenLine \== 0 ){  
        line \= $0;  
        evenLine \= 1;  
    }  
    else {  
        print line ";" $0;  
        evenLine \= 0;  
    }  
}  
OR   
awk 'ORS=NR%2?";":"\\n"'  
OR  
paste \-d';' \- \-

Stampa per le righe con meno di 4 colonne   
awk 'NF\<4{print "Not all scores are available for "$1}' colonne.txt

**GREP**  
grep \-e "\\bthe\\b"  
egrep \-i "\\bthe\\b"  
\# le righe che non contengono that  
grep \-vie "\\bthat\\b"

**PYTHON**

regex\_pattern \= r"^...\\....\\....\\....$" \# Do not delete 'r'.

