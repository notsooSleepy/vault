---
kindle-sync:
  bookId: '37263'
  title: >-
    lpic-1linuxprofessionalinstitutecertificationstudyguideexam101-500andexam102-500_5thedition
  author: Christine Bresnahan
  highlightsCount: 101
---
# lpic-1linuxprofessionalinstitutecertificationstudyguideexam101-500andexam102-500_5thedition
## Metadata
* Author: [[Christine Bresnahan]]

## Highlights
Linux years, to get anything done you had to work with the Gnu/Linux shell. The shell — location: [1592]() ^ref-60959

---
/bin/sh — location: [628]() ^ref-15988

---
Use caution when employing the unset command. If you use it on environment variables, such as PS1, you can cause confusing things to happen. If the variable had a different definition before you modified it, it is  best to change it back to its original setting instead of using unset on the  variable. — location: [760]() ^ref-48816

---
If you want to remove your command-line history, it is fairly easy to do.  First, clear your current history list by typing history -c at the command  line. After that, wipe the history file by issuing the history -w command,  which copies the now blank history list to the .bash_history file, overwriting its contents. — location: [810]() ^ref-43152

---
Table 1.4 shows a few Ex commands that can help you manage your text file. Notice  that all the keystrokes include the necessary colon (:) to use Ex commands.  Tab le 1.4 Commonly used vim Ex mode commands  Keystrokes Description  :! command Execute shell command and display results, but don’t quit editor.  :r! command Execute shell command and include the results in editor buffer area.  :r file Read file contents and include them in editor buffer area. — location: [898]() ^ref-1833

---
ZZ Write buffer to file and quit editor. — location: [908]() ^ref-6837

---
If you need a nicer display than paste can provide, consider using the pr  command. If the files share the same data in a particular field, you can  employ the join command as well. — location: [948]() ^ref-59037

---
Uncovering with od  Occasionally you may need to do a little detective work with files. These situations may  include trying to review a graphics file or troubleshooting a text file that has been modified  by a program. The od utility can help, because it allows you to display a file’s contents in  octal (base — location: [951]() ^ref-48175

---
Counting with wc  The easiest and most common utility for determining counts in a text file is the wc utility. — location: [1062]() ^ref-9398

---
file’s number of lines, words, and bytes in that order. — location: [1064]() ^ref-29807

---
-L --max-line-length Display the byte count of the file’s longest line. — location: [1067]() ^ref-42530

---
An interesting wc option for troubleshooting configuration files is the -L switch.  Generally speaking, line length for a configuration file will be under 150 bytes, though — location: [1069]() ^ref-8029

---
there are exceptions. Thus, if you have just edited a configuration file and that service is no  longer working, check the file’s longest line length. A longer than usual line length indicates  you might have accidently merged two configuration file lines. An example is shown in  Listing 1.43.  Listing 1.43: Using the wc command to check line length  $wc -L /etc/nsswitch.conf  72 /etc/nsswitch.conf — location: [1070]() ^ref-22423

---
Pulling Out Portions with cut — location: [1075]() ^ref-54884

---
Before we delve into using this command, there are few basics to understand concerning  the cut command. They are as follows: — location: [1077]() ^ref-23735

---
cat -E command. — location: [1080]() ^ref-15388

---
If your text file  records end in the ASCII character NUL, you can also use cut on them, but you must use  the -z option. — location: [1080]() ^ref-5338

---
For some of the cut command options to be properly used,  fields must exist within each text file record. These fields are not database-style fields but  instead data that is separated by some delimiter. A delimiter is one or more characters that  create a boundary between different data items within a record. A single space can be a  delimiter. The password file, /etc/passwd, uses colons (:) to separate data items within a  record. — location: [1082]() ^ref-57396

---
Because the uniq utility recognizes only repeated lines that are one after the other in a text file, only one of the C text  lines is removed from the display. The two A lines are still both shown. — location: [1105]() ^ref-38271

---
A malicious attacker can create two files that have the same MD5 hash  value. However, at this point in time, a file that is not under the attacker’s  control cannot have its MD5 hash value modified. Therefore, it is imperative that you have checks in place to ensure that your file was not created  by a third-party malicious user. An even better solution is to use a stronger  hash algorithm. — location: [1113]() ^ref-26607

---
The sha512sum utility uses the SHA-512 algorithm, which is the best to use for  security purposes and is typically employed to hash salted passwords in the /etc/shadow  file on Linux. — location: [1126]() ^ref-22825

---
You can use these SHA utilities, just like the md5sum program was used in Listing 1.46,  to ensure a file’s integrity when it is transferred. That way, file corruption is avoided as well  as any malicious modifications to the file. — location: [1128]() ^ref-26891

---
Using Regular Expressions  Many commands use regular expressions. A regular expression is a pattern template you  define for a utility such as grep, which then uses the pattern to filter text. Employing regular expressions along with text-filtering commands expands your mastery of the Linux  command line.  Using grep — location: [1129]() ^ref-6425

---
The grep command’s commonly used options  Short Long Description  -c --count Display a count of text file records that contain a  PATTERN match.  -d action --directories=action When a file is a directory, if action is set to read,  read the directory as if it were a regular text file;  if action is set to skip, ignore the directory; and  if action is set to recurse, act as if the - R, -r, or  --recursive option was used.  -E --extended-regexp Designate the PATTERN as an extended regular  expression.  -i --ignore-case Ignore the case in the PATTERN as well as in any  text file records.  -R, -r --recursive Search a directory’s contents, and for any subdirectory within the original directory tree, consecutively search its contents as well (recursively).  -v --invert-match Display only text files records that do not contain a  PATTERN match. — location: [1134]() ^ref-27520

---
Using a simple grep command to search a file  $grep root /etc/passwd  root:x:0:0:root:/root:/bin/bash  operator:x:11:0:operator:/root:/sbin/nologin — location: [1143]() ^ref-31747

---
Notice that the grep command returns each file record (line) that contains an instance of  the PATTERN, which in this case was the word root. — location: [1144]() ^ref-27387

---
Using the grep command to search for patterns stored in a text file  $cat accounts.txt  sshd  Christine  nfsnobody  $  $fgrep -f accounts.txt /etc/passwd  sshd:x:74:74:Privilege-separated SSH:/var/empty/sshd:/sbin/nologin  Christine:x:1001:1001::/home/Christine:/bin/bash  nfsnobody:x:65534:65534:Anonymous NFS User:/var/lib/nfs:/sbin/nologin  $  $grep -F -f accounts.txt /etc/passwd  sshd:x:74:74:Privilege-separated SSH:/var/empty/sshd:/sbin/nologin  Christine:x:1001:1001::/home/Christine:/bin/bash  nfsnobody:x:65534:65534:Anonymous NFS User:/var/lib/nfs:/sbin/nologin — location: [1146]() ^ref-59365

---
Also notice in Listing 1.49 that the third command is the grep -F command. The  grep -F command is equivalent to using the fgrep command, which is why the two commands produce identical results. — location: [1153]() ^ref-43169

---
(.*) to represent multiple characters and a single dot (.) to represent one character. — location: [1156]() ^ref-50274

---
They  also may use brackets to represent multiple characters, such as [a,e,i,o,u] (you do not  have to include the commas) or a range of characters, such as [A-z]. When brackets are  employed, it is called a bracket expression. — location: [1157]() ^ref-39057

---
To find text file records that begin with particular characters, you can precede them  with a caret (^) symbol. For finding text file records where particular characters are at  the record’s end, append them with a dollar sign ($) symbol. Both the caret and the dollar  sign symbols are called anchor characters for BREs, because they fasten the pattern to the  beginning or the end of a text line. — location: [1158]() ^ref-58013

---
The -v option is useful when auditing your configuration files with the grep utility. It  produces a list of text file records that do not contain the pattern. Listing 1.52 shows an  example of finding all the records in the password file that do not end in nologin. Notice  that the BRE pattern puts the $at the end of the word. If you were to place the $before the  word, it would be treated as a variable name instead of a BRE pattern.  Listing 1.52: Using the grep command to audit the password file  $grep -v nologin$ /etc/passwd  root:x:0:0:root:/root:/bin/bash  sync:x:5:0:sync:/sbin:/bin/sync  […]  Christine:x:1001:1001::/home/Christine:/bin/bash — location: [1175]() ^ref-36263

---
If you need to filter out all the blank lines in a file (display only lines with  text), use grep with the -v option to invert the matching pattern. Then  employ the ^ and $anchor characters like grep -v ^$ filename at the  command line. — location: [1180]() ^ref-54211

---
Commonly used character classes  Class Description  [:alnum:] Matches any alphanumeric characters (any case), and is equal to using  the [0-9A-Za-z] bracket expression  [:alpha:] Matches any alphabetic characters (any case), and is equal to using the  [A-Za-z] bracket expression — location: [1185]() ^ref-43349

---
Class Description  [:blank:] Matches any blank characters, such as tab and space  [:digit:] Matches any numeric characters, and is equal to using the [0-9] bracket  expression  [:lower:] Matches any lowercase alphabetic characters, and is equal to using the  [a-z] bracket expression  [:punct:] Matches punctuation characters, such as!, #, $, and @  [:space:] Matches space characters, such as tab, form feed, and space  [:upper:] Matches any uppercase alphabetic characters, and is equal to using the  [A-Z] bracket expression — location: [1187]() ^ref-10388

---
Notice the extra brackets needed to properly use a character class. Thus, to use [:digit:],  you must type [[:digit:]] when employing this character class with the grep command.  If you need to search for a character in a file that has special meaning in  an expression or at the command line, such as the $anchor character, precede it with a backslash (\). This lets the grep utility know you are searching for that character and not using it in an expression. — location: [1194]() ^ref-56765

---
Understanding Extended Regular Expressions  Extended regular expressions (EREs) allow more complex patterns. For example, a vertical  bar symbol (|) allows you to specify two possible words or character sets to match. You can  also employ parentheses to designate additional subexpressions.  Using ERE patterns can be rather tricky. A few examples employing grep with EREs are  helpful, such as the ones shown in Listing 1.54.  Listing 1.54: Using the grep command with an ERE pattern  $grep -E "^root|^dbus" /etc/passwd  root:x:0:0:root:/root:/bin/bash  dbus:x:81:81:System message bus:/:/sbin/nologin  $  $egrep "(daemon|s).*nologin" /etc/passwd  bin:x:1:1:bin:/bin:/sbin/nologin  daemon:x:2:2:daemon:/sbin:/sbin/nologin  […]  $  In the first example, the grep command uses the -E option to indicate the pattern is an  extended regular expression. If you did not employ the -E option, unpredictable results  would occur. Quotation marks around the ERE pattern protect it from misinterpretation.  The command searches for any password file records that start with either the word root  or the word dbus. Thus, a caret (^) is placed prior to each word, and a vertical bar (|) separates the words to indicate that the record can start with either word.  In the second example in Listing 1.54, notice that the egrep command is employed. The  egrep command is equivalent to using the grep -E command. The ERE pattern here also  uses quotation marks to avoid misinterpretation and employs parentheses to issue a subexpression. The subexpression consists of a choice, indicated by the vertical bar (|), between  the word daemon and the letter s. Also in the ERE pattern, the .* symbols are used to indicate there can be anything in between the subexpression choice and the word nologin in  the text file record.  Take a deep breath. That was a lot to take in. However, as hard as BRE and ERE patterns are, they are worth using with the grep command to filter out data from your text files. — location: [1198]() ^ref-55080

---
Listing 1.1: Showing to which shell /bin/sh points on a CentOS distribution  $readlink /bin/sh  bash  $  It is always a good idea to check which shell the file is linked to. In Listing 1.2, you can  see that the /bin/sh file is a symbolic link to the Dash shell (dash). — location: [627]() ^ref-59750

---
Listing 1.2: Showing to which shell /bin/sh points on an Ubuntu distribution  $readlink /bin/sh  dash — location: [629]() ^ref-23539

---
Listing 1.3: Displaying the current shell on a CentOS distribution  $echo $SHELL  /bin/bash  $  $echo $BASH_VERSION  4.2.46(2)-release — location: [634]() ^ref-32780

---
$uname -a  Linux Ubuntu1804 4.15.0-46-generic # 49-Ubuntu SMP Wed Feb 6  09:33:07 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux — location: [639]() ^ref-36957

---
Listing 1.9: Using the cd and pwd commands  $pwd  /home/Christine  $  $cd /etc  $pwd  /etc — location: [676]() ^ref-27385

---
Listing 1.12: Using type to determine whether a command is external or internal  $type echo  echo is a shell builtin  $  $type pwd  pwd is a shell builtin  $  $type uname  uname is /usr/bin/uname — location: [696]() ^ref-38969

---
Listing 1.13: Using set to display active environment variables  $set  […]  BASH=/bin/bash  […]  HISTFILE=/home/Christine/.bash_history  […]  HISTSIZE=1000  HOME=/home/Christine  HOSTNAME=localhost.localdomain  […]  PS1='$ '  PS2='> '  […]  SHELL=/bin/bash  […]  $  Besides the set utility, you can also employ the env and printenv commands to display variables. The env and printenv utilities allow you to see  locally defined variables, such as those created in a shell script (covered in  Chapter 9) as well as environment variables. — location: [716]() ^ref-50994

---
The which utility is helpful in these cases. It searches through the PATH directories to  find the program. If it locates the program, it displays its absolute directory reference. This  saves you from having to look through the PATH variable’s output yourself, as Listing 1.16  shows.  Listing 1.16: Using the which utility  $which Hello.sh  /usr/bin/which: no Hello.sh in (/usr/local/bin:/usr/bin:  /usr/local/sbin:/usr/sbin:/home/Christine/.local/bin:/home/Christine/bin)  $  $which echo  /usr/bin/echo — location: [729]() ^ref-61350

---
Listing 1.20: Using export to preserve an environment variable’s definition  My new prompt: export PS1="KeepPrompt: "  KeepPrompt:  KeepPrompt: bash  KeepPrompt:  KeepPrompt: echo $SHLVL  2  KeepPrompt:  KeepPrompt: PS1="$ "  $export PS1 — location: [753]() ^ref-24219

---
Listing 1.22: Using the man -k command to search for keywords  $man -k passwd  […]  passwd (1) - update user's authentication tokens  […]  passwd (5) - password file  […]  smbpasswd (5) - The Samba encrypted password file  […]  $  Instead of man -k, you can use the apropos command. For example, enter  apropos passwd at the command line. However, man -k is easier to type. — location: [775]() ^ref-46660

---
Listing 1.23: Using the history command to view recent commands  $history  […]  915 echo $EDITOR  916 export EDITOR=nano  917 echo $EDITOR  918 unset EDITOR  919 echo $EDITOR  920 man -k passwd  […] — location: [791]() ^ref-3207

---
Listing 1.24: Reexecuting commands in the command history  $!920  man -k passwd  […]  passwd (1) - update user's authentication tokens  […]  passwd (5) - password file  […] — location: [794]() ^ref-8900

---
Listing 1.25: Viewing the history filename  $echo $HISTFILE  /home/Christine/.bash_history — location: [804]() ^ref-56162

---
TabLE 1.6 The cat command’s commonly used options  Short Long Description  -A --show-all Equivalent to using the option -vET combination.  -E --show-ends Display a $when a newline linefeed is encountered.  -n --number Number all text file lines and display that number in the output.  -s --squeeze-blank Do not display repeated blank empty text file lines.  -T --show-tabs Display a ^I when a tab character is encountered.  -v --show-nonprinting Display nonprinting characters when encountered using  either ^ and/or M- notation. — location: [931]() ^ref-10236

---
Separating with split  One nice command to use is split. This utility allows you to divide a large file into smaller  chunks, which is handy when you want to quickly create a smaller text file for testing purposes. — location: [968]() ^ref-45754

---
Organizing with sort  The sort utility sorts a file’s data. Keep in mind that it makes no changes to the original  file; only the output is sorted. — location: [982]() ^ref-48158

---
Numbering with nl  Another useful file-formatting command is the nl utility (number line utility). This little  command allows you to number lines in a text file in powerful ways. It even allows you to  use regular expressions (covered later in this chapter) to designate which lines to number. — location: [993]() ^ref-53310

---
The less pager utility allows faster file traversal because it does not read the entire file  prior to displaying the file’s first page. — location: [1014]() ^ref-499

---
By default, the Linux man page utility uses less as its pager. Learning the  less utility’s commands will allow you to search through various manual  pages with ease. — location: [1019]() ^ref-30665

---
One of the most useful tail utility features is its ability to watch log files. Log files typically have new messages appended to the file’s bottom. Watching new messages as they are  added is very handy. Use the -f (or --follow) switch on the tail command and provide the  log filename to watch as the command’s argument. — location: [1047]() ^ref-25007

---
Some log files have been replaced on various Linux distributions, and now  the messages are kept in a journal file managed by journald. To watch  messages being added to the journal file, use the journalctl --follow  command. — location: [1051]() ^ref-57243

---
Listing 1.41: Watching a log file with the tail command  $sudo tail -f /var/log/auth.log  [sudo] password for Christine:  Aug 27 10:15:14 Ubuntu1804 sshd[15662]: Accepted password […]  Aug 27 10:15:14 Ubuntu1804 sshd[15662]: pam_unix(sshd:sess[…]  Aug 27 10:15:14 Ubuntu1804 systemd-logind[588]: New sessio[…]  Aug 27 10:15:50 Ubuntu1804 sudo: Christine: TTY=pts/1; P[…]  Aug 27 10:15:50 Ubuntu1804 sudo: pam_unix(sudo:session): s[…]  Aug 27 10:16:21 Ubuntu1804 login[10703]: pam_unix(login:se[…]  Aug 27 10:16:21 Ubuntu1804 systemd-logind[588]: Removed se[…] — location: [1054]() ^ref-20319

---
TabLE 1.7 The wc command’s commonly used options  Short Long Description  -c --bytes Display the file’s byte count.  -L --max-line-length Display the byte count of the file’s longest line.  -l --lines Display the file’s line count.  -m --chars Display the file’s character count.  -w --words Display the file’s word count.  An interesting wc option for troubleshooting configuration files is the -L switch.  Generally speaking, line length for a configuration file will be under 150 bytes, though — location: [1066]() ^ref-57082

---
When you issue the wc command with no options and pass it a filename, the utility will  display the file’s number of lines, words, and bytes in that order. Listing 1.42 shows an  example.  Listing 1.42: Employing the wc command  $wc random.txt  5 9 52 random.txt — location: [1063]() ^ref-39963

---
Text File Records A text file record is a single-file line that ends in a newline linefeed,  which is the ASCII character LF. You can see if your text file uses this end-of-line character via the cat -E command. It will display every newline linefeed as a $. If your text file  records end in the ASCII character NUL, you can also use cut on them, but you must use  the -z option.  Text File Record Delimiter For some of the cut command options to be properly used,  fields must exist within each text file record. These fields are not database-style fields but  instead data that is separated by some delimiter. A delimiter is one or more characters that  create a boundary between different data items within a record. A single space can be a  delimiter. The password file, /etc/passwd, uses colons (:) to separate data items within a  record. — location: [1078]() ^ref-25952

---
The cut command’s commonly used options  Short Long Description  -c nlist --characters nlist Display only the record characters in the nlist (e.g.,  1–5).  -b blist --bytes blist Display only the record bytes in the blist (e.g., 1–2).  -d d --delimiter d Designate the record’s field delimiter as d. This overrides the Tab default delimiter. Put d within quotation  marks to avoid unexpected results.  -f flist --fields flist Display only the record’s fields denoted by flist  (e.g., 1,3).  -s --only-delimited Display only records that contain the designated  delimiter.  -z --zero-terminated Designate the record end-of-line character as the ASCII  character NUL.  A cut command in action is shown in Listing 1.44.  Listing 1.44: Employing the cut command  $head -2 /etc/passwd  root:x:0:0:root:/root:/bin/bash  bin:x:1:1:bin:/bin:/sbin/nologin  $  $cut -d":" -f 1,7 /etc/passwd  root:/bin/bash  bin:/sbin/nologin — location: [1088]() ^ref-31437

---
Discovering Repeated Lines with uniq  A quick way to find repeated lines in a text file is with the uniq utility. Just type uniq and  follow it with the filename whose contents you want to check.  The uniq utility will find repeated text lines only if they come right after one another.  Used without any options, the command will display only unique (non-repeated) lines. An  example of using this command is shown in Listing 1.45.  Listing 1.45: Using the uniq command  $cat NonUniqueLines.txt  A  C  C  A  $  $uniq NonUniqueLines.txt  A  C  A  $  Notice that in the cat command’s output there are actually two sets of repeated lines in  this file. One set is the C lines, and the other set is the A lines. Because the uniq utility recognizes only repeated lines that are one after the other in a text file, only one of the C text  lines is removed from the display. The two A lines are still both shown. — location: [1100]() ^ref-4421

---
Digesting an MD5 Algorithm  The md5sum utility is based on the MD5 message-digest algorithm. It was originally created  to be used in cryptography. It is no longer used in such capacities due to various known  vulnerabilities. However, it is still excellent for checking a file’s integrity. — location: [1107]() ^ref-14550

---
Listing 1.46: Using md5sum to check the original file  $md5sum fourtytwo.txt  0ddaa12f06a2b7dcd469ad779b7c2a33 fourtytwo.txt — location: [1109]() ^ref-65380

---
Securing Hash Algorithms  The Secure Hash Algorithms (SHA) is a family of various hash functions. Though typically  used for cryptography purposes, they can also be used to verify a file’s integrity after it is  copied or moved to another location.  Several utilities implement these various algorithms on Linux. The quickest way to find  them is via the method shown in Listing 1.47. Keep in mind your particular distribution  may store them in the /bin directory instead.  Listing 1.47: Looking at the SHA utility names  $ls -1 /usr/bin/sha???sum  /usr/bin/sha224sum  /usr/bin/sha256sum  /usr/bin/sha384sum  /usr/bin/sha512sum — location: [1116]() ^ref-56697

---
Understanding Basic Regular Expressions  Basic regular expressions (BREs) include characters, such as a dot followed by an asterisk  (.*) to represent multiple characters and a single dot (.) to represent one character. They  also may use brackets to represent multiple characters, such as [a,e,i,o,u] (you do not  have to include the commas) or a range of characters, such as [A-z]. When brackets are  employed, it is called a bracket expression.  To find text file records that begin with particular characters, you can precede them  with a caret (^) symbol. For finding text file records where particular characters are at  the record’s end, append them with a dollar sign ($) symbol. Both the caret and the dollar  sign symbols are called anchor characters for BREs, because they fasten the pattern to the  beginning or the end of a text line. — location: [1155]() ^ref-46415

---
Using a BRE pattern is fairly straightforward with the grep utility. Listing 1.51 shows  some examples.  Listing 1.51: Using the grep command with a BRE pattern  $grep daemon.*nologin /etc/passwd  daemon:x:2:2:daemon:/sbin:/sbin/nologin  […]  daemon:/dev/null:/sbin/nologin  […]  $  $grep root /etc/passwd  root:x:0:0:root:/root:/bin/bash  operator:x:11:0:operator:/root:/sbin/nologin  $  $grep ^root /etc/passwd  root:x:0:0:root:/root:/bin/bash — location: [1163]() ^ref-31034

---
For using character classes with the grep command, enclose the bracketed character  class in another set of brackets. — location: [1191]() ^ref-49441

---
Listing 1.53: Using the grep command and a character class — location: [1193]() ^ref-42874

---
$grep [[:digit:]] random.txt  42  0010 1010  0000 0010 — location: [1194]() ^ref-25998

---
Handling Standard Output  It is important to know that Linux treats every object as a file. This includes the output  process, such as displaying a text file on the screen. Each file object is identified using a file  descriptor, an integer that classifies a process’s open files. The file descriptor that identifies  output from a command or script file is 1. It is also identified by the abbreviation STDOUT,  which describes standard output.  By default, STDOUT directs output to your current terminal. Your process’s current terminal is represented by the /dev/tty file.  A simple command to use when discussing standard output is the echo command. Issue  the echo command along with a text string, and the text string will display to your process’s  STDOUT, which is typically the terminal screen. — location: [1218]() ^ref-46204

---
Redirecting Standard Error  Another handy item to redirect is standard error. The file descriptor that identifies a command or script file error is 2. It is also identified by the abbreviation STDERR, which  describes standard error. STDERR, like STDOUT, is by default sent to your terminal  (/dev/tty).  The basic redirection operator to send STDERR to a file is the 2> operator. If you need  to append the file, use the 2>> operator. — location: [1242]() ^ref-55443

---
$grep -d skip hosts: /etc/* 2> err.txt  /etc/nsswitch.conf:#hosts: db files nisplus nis dns  /etc/nsswitch.conf:hosts: files dns myhostname  […]  $  $cat err.txt  grep: /etc/anacrontab: Permission denied  grep: /etc/audisp: Permission denied — location: [1248]() ^ref-46618

---
Sometimes you want to send standard error and standard output to the  same file. In these cases, use the &> redirection operator to accomplish  your goal. — location: [1255]() ^ref-44321

---
If you don’t care to keep a copy of the error messages, you can always throw them away.  This is done by redirecting STDERR to the /dev/null file as shown snipped in Listing 1.59.  Listing 1.59: Using a STDERR redirection operator to remove error messages  $grep -d skip hosts: /etc/* 2> /dev/null  /etc/nsswitch.conf:#hosts: db files nisplus nis dns  /etc/nsswitch.conf:hosts: — location: [1256]() ^ref-12040

---
Regulating Standard Input  Standard input, by default, comes into your Linux system via the keyboard and/or other  input devices. The file descriptor that identifies an input into a command or script file is 0.  It is also identified by the abbreviation STDIN, which describes standard input. — location: [1260]() ^ref-60213

---
As with STDOUT and STDERR, you can redirect STDIN. The basic redirection operator is the < symbol. The tr command is one of the few utilities that require you to redirect  standard input. An example is shown in Listing 1.60.  Listing 1.60: Employing an STDIN redirection operator  $cat Grades.txt  89 76 100 92 68 84 73  $  $tr " ""," < Grades.txt  89,76,100,92,68,84,73  $  In Listing 1.60, the file Grades.txt contains various integers separated by a space. The  second command utilizes the tr utility to change each space into a comma (,). Because the tr  command requires the STDIN redirection symbol, it is also employed in the second command  followed by the filename. Keep — location: [1263]() ^ref-57657

---
le 1.11 Commonly used redirection operators  Operator Description  > Redirect STDOUT to specified file. If file exists, overwrite it. If it does not  exist, create it.  >> Redirect STDOUT to specified file. If file exists, append to it. If it does not  exist, create it.  2> Redirect STDERR to specified file. If file exists, overwrite it. If it does not  exist, create it.  2>> Redirect STDERR to specified file. If file exists, append to it. If it does not  exist, create it.  &> Redirect STDOUT and STDERR to specified file. If file exists, overwrite it. If it  does not exist, create it.  &>> Redirect STDOUT and STDERR to specified file. If file exists, append to it. If it  does not exist, create it.  < Redirect STDIN from specified file into command.  <> Redirect STDIN from — location: [1270]() ^ref-4263

---
In cases where you want to keep a copy of the command pipeline’s output as well as view  it, the tee command will help. Similar to a tee pipe fitting in plumbing, where the water  flow is sent in multiple directions, the tee command allows you to both save the output to a  file and display it to STDOUT. — location: [1297]() ^ref-43845

---
Listing 1.63: Employing the tee command  $grep /bin/bash$ /etc/passwd | tee BashUsers.txt  root:x:0:0:root:/root:/bin/bash  user1:x:1000:1000:Student User One:/home/user1:/bin/bash  Christine:x:1001:1001::/home/Christine:/bin/bash  $  $cat BashUsers.txt  root:x:0:0:root:/root:/bin/bash  user1:x:1000:1000:Student User One:/home/user1:/bin/bash  Christine:x:1001:1001::/home/Christine:/bin/bash — location: [1299]() ^ref-18727

---
Using sed  Another interesting command-line program is a stream editor. There are times where you  will want to edit text without having to pull out a full-fledged text editor. A stream editor  modifies text that is passed to it via a file or output from a pipeline. This editor uses special  commands to make text changes as the text “streams” through the editor utility.  The command to invoke the stream editor is sed. The sed utility edits a stream of text  data based on a set of commands you supply ahead of time. It is a very quick editor because  it makes only one pass through the text to apply the modifications.  The sed editor changes data based on commands either entered into the command line  or stored in a text file. The process the editor goes through is as follows:  1. Reads one text line at a time from the input stream  2. Matches that text with the supplied editor commands  3. Modifies the text as specified in the commands  4. Displays the modified text — location: [1306]() ^ref-22730

---
Listing 1.64: Using sed to modify STDIN text  $echo "I like cake." | sed 's/cake/donuts/'  I like donuts. — location: [1317]() ^ref-64027

---
(substitute) — location: [1319]() ^ref-38065

---
Listing 1.65: Using sed to globally modify STDIN text  $echo "I love cake and more cake." | sed 's/cake/donuts/'  I love donuts and more cake.  $  $echo "I love cake and more cake." | sed 's/cake/donuts/g'  I love donuts and more donuts. — location: [1323]() ^ref-8869

---
$sed 's/cake/donuts/' cake.txt  Christine likes chocolate donuts.  Rich likes lemon donuts.  Tim only likes yellow donuts.  Samantha does not like donuts.  $  $cat cake.txt  Christine likes chocolate cake.  Rich likes lemon cake.  Tim only likes yellow cake.  Samantha does not like cake. — location: [1329]() ^ref-35024

---
It may be tempting to think that the sed utility is operating on the text file  as a whole, but it is not. The stream editor applies its commands to each  text file line individually. Thus, in our previous example, if the word cake  was found multiple times within a single text file line, you’d need to use the  g global command to change all instances. — location: [1334]() ^ref-60721

---
Listing 1.67: Using sed to delete file text  $sed '/Christine/d' cake.txt  Rich likes lemon cake.  Tim only likes yellow cake.  Samantha does not like cake. — location: [1340]() ^ref-23034

---
You can also change an entire line of text. To accomplish this, you use the syntax of  ' ADDRESS c NEWTEXT' for the sed command’s SCRIPT. The ADDRESS refers to the file’s line — location: [1341]() ^ref-53023

---
number, and the NEWTEXT is the different text line you want displayed. An example of this  method is shown in Listing 1.68.  Listing 1.68: Using sed to change an entire file line  $sed '4cI am a new line' cake.txt  Christine likes chocolate cake.  Rich likes lemon cake.  Tim only likes yellow cake.  I am a new line — location: [1343]() ^ref-51873

---
Tab le 1.12 The sed command’s commonly used options  Short Long Description  -e script --expression=script Add commands in script to text processing. The  script is written as part of the sed command.  -f script --file=script Add commands in script to text processing. The  script is a file.  -r --regexp-extended Use extended regular expressions in script. — location: [1346]() ^ref-45129

---
Listing 1.69: Using sed -e to use multiple scripts  $sed -e 's/cake/donuts/; s/like/love/' cake.txt  Christine loves chocolate donuts.  Rich loves lemon donuts.  Tim only loves yellow donuts.  Samantha does not love donuts. — location: [1350]() ^ref-11804

---
Listing 1.70: Employing the xargs command  $touch EmptyFile1.txt EmptyFile2.txt EmptyFile3.txt  $  $ls EmptyFile?.txt  EmptyFile1.txt EmptyFile2.txt EmptyFile3.txt  $  $ls -1 EmptyFile?.txt | xargs -p /usr/bin/rm  /usr/bin/rm EmptyFile1.txt EmptyFile2.txt EmptyFile3.txt ?...n — location: [1358]() ^ref-50041

---
The output from the ls command is piped as STDIN into the xargs utility.  The xargs command uses the -p option. This option causes the xargs utility to stop and ask  permission before enacting the constructed command-line command. Notice that the absolute  directory reference for the rm command is used — location: [1362]() ^ref-717

---
The created command, in Listing 1.70, attempts to remove all three empty files with one  rm command. — location: [1365]() ^ref-14986

---
Listing 1.71: Using the $() method to create commands  $rm -i $(ls EmptyFile?.txt)  rm: remove regular empty file ‘EmptyFile1.txt’? y  rm: remove regular empty file ‘EmptyFile2.txt’? y  rm: remove regular empty file ‘EmptyFile3.txt’? y — location: [1369]() ^ref-24946

---
Another method to created command-line commands on the fly uses shell expansion. — location: [1367]() ^ref-54004

---
Exam Essentials  Express the different basic shell concepts. The shell program provides the command-line  prompt, which can be reached through a tty terminal or by employing a GUI terminal  emulator. There are multiple shell programs, but the most popular is the Bash shell, which  is typically located in the /bin/bash file. The /bin/sh file is often linked to the Bash shell  program, but it may be linked to other shells, such as the Dash shell (/bin/dash). The shell  in use can be checked via displaying the SHELL environment variable’s contents with the  echo utility. The current Linux kernel can be shown with the uname -a command.  Summarize the various utilities that can be employed to read text files. To read entire  small text files, you can use the cat and bat utilities. If you need to read only the first or  last lines of a text file, employ either the head or tail command. For a single text line out  of a file, the grep utility is useful. For reviewing a file a page at a time, you can use either  the less or the more pager utility.  Describe the various methods used for editing text. Editing text files is part of a system  administrator’s life. You can use full-screen editors such as the rather complicated vim text  editor or the simple and easy-to-use nano editor. For fast and powerful text stream editing,  employ the use of sed and its scripts.  Summarize the various utilities used in processing text files. Filtering text file data can  be made much easier with utilities such as grep, egrep, fgrep, and cut. Once that data is  filtered, you may want to format it for viewing using sort, nl, or even the cat utility. If you  need some statistical information on your text file, such as the number of lines it contains,  the wc command is handy.  Explain both the structures and commands for redirection. Employing STDOUT,  STDERR, and STDIN redirection allows rather complex filtering and processing of text.  The echo command can assist in this process. You can also use pipelines of commands to  perform redirection and produce excellent data for review. In addition, pipelines can be  used in creating commands on the fly with utilities, such as xargs. — location: [1377]() ^ref-43265

---
