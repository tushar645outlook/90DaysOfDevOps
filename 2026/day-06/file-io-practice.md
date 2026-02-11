**Creation of new file**

ubuntu@ip-192-168-0-93:~$ ls
notes.txt

============================================================================================================================================================================

**Write lines using redirection**
**Overwrite / first write (>)**

ubuntu@ip-192-168-0-93:~$ echo "Line 1: Linux file operations practice through TWS" > notes.txt
ubuntu@ip-192-168-0-93:~$ cat notes.txt
Line 1: Linux file operations practice through TWS

Append (>>)

ubuntu@ip-192-168-0-93:~$ echo "Line 2: Using redirection operators" >> notes.txt
ubuntu@ip-192-168-0-93:~$ cat notes.txt
Line 1: Linux file operations practice through TWS
Line 2: Using redirection operators

ubuntu@ip-192-168-0-93:~$ cat notes.txt
Line 1: Linux file operations practice through TWS
Line 2: Using redirection operators
Line 3: Appending data safely

At this point, the file has 3 lines.
=============================================================================================================================================================

**Use tee to write and display**

ubuntu@ip-192-168-0-93:~$ echo "Line 4: Written using tee command" | tee -a notes.txt
Line 4: Written using tee command

==============================================================================================================================================================

**Add a few more lines (keep total 8–12)**

ubuntu@ip-192-168-0-93:~$ echo "Line 5: cat reads entire file" >> notes.txt
echo "Line 6: head reads from the top" >> notes.txt
echo "Line 7: tail reads from the bottom" >> notes.txt
echo "Line 8: End of practice notes" >> notes.txt

=================================================================================================================================================================

**Read the full file**

ubuntu@ip-192-168-0-93:~$ cat notes.txt
Line 1: Linux file operations practice through TWS
Line 2: Using redirection operators
Line 3: Appending data safely
Line 4: Written using tee command
Line 5: cat reads entire file
Line 6: head reads from the top
Line 7: tail reads from the bottom
Line 8: End of practice notes

====================================================================================================================================================================

**Read partial content**
**Top 2 lines**

ubuntu@ip-192-168-0-93:~$ head -n 2 notes.txt
Line 1: Linux file operations practice through TWS
Line 2: Using redirection operator

**Last 2 lines**

ubuntu@ip-192-168-0-93:~$ tail -n 2 notes.txt
Line 7: tail reads from the bottom
Line 8: End of practice notes

==========================================================================================================================================================================
