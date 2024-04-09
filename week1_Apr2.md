# Week 1 Lab Report
## cd
<ol>
<li><p> Command with no arguments </p>
  <pre><code>
    (base) ➜  lecture1 git:(＜PA3＞) ✗ cd
    (base) ➜  ~ git:(＜PA3＞) ✗ pwd
    /Users/admin
  </code></pre>
</li>

<blockquote>
  The command changes the current directory to the <code>User/admin</code> folder, which is a home directory.
 <br>working directory: <code>User/admin</code>
</blockquote>

<li><p> Command with path to a directory as an argument </p>
  <pre><code>
    (base) ➜  CSE 15L git:(＜PA3＞) ✗ cd lecture1                
    (base) ➜  lecture1 git:(＜PA3＞) ✗ cd temp
    cd: no such file or directory: temp
    (base) ➜  lecture1 git:(＜PA3＞) ✗ pwd
    /Users/admin/Documents/Documents_Minseo_Chu_MacBook/ucsd_docs/CSE 15L/lecture1
  </code></pre>
</li>

<blockquote>
 The command changes the current directory to the inputted directory path.
 <br>If there isn't a matching directory in the path, it prints out an error message: "cd: no such file or directory: (inputted directory's name)"
  <br>working directory: <code>/Users/admin/Documents/Documents_Minseo_Chu_MacBook/ucsd_docs/CSE 15L/lecture1</code>
</blockquote>

<li><p> Command with path to a file as an argument </p>
  <pre><code>
    (base) ➜  lecture1 git:(main) ✗ cd '/Users/admin/Documents/Documents_Minseo_Chu_MacBook/ucsd_docs/CSE 15L/Hello.java'
    cd: not a directory: /Users/admin/Documents/Documents_Minseo_Chu_MacBook/ucsd_docs/CSE 15L/Hello.java
  </code></pre>
</li>

<blockquote>
  The command prints out an error message "cd: not a directory" since file is not a directory.
  <br>working directory: <code>/Users/admin/Documents/Documents_Minseo_Chu_MacBook/ucsd_docs/CSE 15L/lecture1</code>
</blockquote>

</ol>

## ls
<ol>
<li><p> Command with no arguments </p>
  <pre><code>
    (base) ➜  CSE 15L git:(＜PA3＞) ✗ ls
    Hello.class Hello.java  lecture1    test.java
    (base) ➜  CSE 15L git:(＜PA3＞) ✗ pwd
    /Users/admin/Documents/Documents_Minseo_Chu_MacBook/ucsd_docs/CSE 15L
  </code></pre>
</li>

<blockquote>
  The command prints the list of files in the current directory.
  <br>working directory: <code>/Users/admin/Documents/Documents_Minseo_Chu_MacBook/ucsd_docs/CSE 15L</code>
</blockquote>
  
<li><p> Command with path to a directory as an argument </p>
  <pre><code>
    (base) ➜  CSE 15L git:(＜PA3＞) ✗ ls lecture1
    README   messages
    (base) ➜  CSE 15L git:(＜PA3＞) ✗ ls temp
    ls: temp: No such file or directory
    (base) ➜  CSE 15L git:(＜PA3＞) ✗ pwd
    /Users/admin/Documents/Documents_Minseo_Chu_MacBook/ucsd_docs/CSE 15L
  </code></pre>
</li>

<blockquote>
  The command prints the list of files in the directory referring to the inputted directory path, but doesn't change the working directory.
  <br> If the isn't a corresponding directory, it gives out error: "ls: (directory name): No such file or directory"
  <br>working directory: <code>/Users/admin/Documents/Documents_Minseo_Chu_MacBook/ucsd_docs/CSE 15L`</code>
</blockquote>
  
<li><p> Command with path to a file as an argument </p>
  <pre><code>
    (base) ➜  CSE 15L git:(＜PA3＞) ✗ ls Hello.java
    Hello.java
    (base) ➜  CSE 15L git:(＜PA3＞) ✗ ls temp.java 
    ls: temp.java: No such file or directory
    (base) ➜  CSE 15L git:(＜PA3＞) ✗ pwd
    /Users/admin/Documents/Documents_Minseo_Chu_MacBook/ucsd_docs/CSE 15L
  </code></pre>
</li>

<blockquote>
  The command prints the name of file in the inputted path, but doesn't change the working directory.
  <br> If the isn't a corresponding directory, it gives out error: "ls: (file name) : No such file or directory"
  <br>
  <br>working directory: <code>/Users/admin/Documents/Documents_Minseo_Chu_MacBook/ucsd_docs/CSE 15L</code>
</blockquote>

</ol>

## cat
<ol>
<li><p> Command with no arguments </p>
  <pre><code>
    (base) ➜  CSE 15L git:(master) ✗ cat
    hello
    hello
    ^C
    (base) ➜  CSE 15L git:(master) ✗ pwd
    /Users/admin/Documents/Documents_Minseo_Chu_MacBook/ucsd_docs/CSE 15L
  </code></pre>
</li>

<blockquote>
  The command prints the content the user inputted in the terminal
  <br>working directory: <code>/Users/admin/Documents/Documents_Minseo_Chu_MacBook/ucsd_docs/CSE 15L</code>
</blockquote>
  
<li><p> Command with path to a directory as an argument </p>
  <pre><code>
    (base) ➜  CSE 15L git:(master) ✗ cat lecture1
    cat: lecture1: Is a directory
    (base) ➜  CSE 15L git:(master) ✗ pwd                         
    /Users/admin/Documents/Documents_Minseo_Chu_MacBook/ucsd_docs/CSE 15L
  </code></pre>
</li>

<blockquote>
  The command prints error message "cat: (directory's name): Is a directory".
  <br>working directory: <code>/Users/admin/Documents/Documents_Minseo_Chu_MacBook/ucsd_docs/CSE 15L`</code>
</blockquote>
  
<li><p> Command with path to a file as an argument </p>
  <pre><code>
    (base) ➜  CSE 15L git:(＜PA3＞) ✗ cat lecture1/messages/ko.txt
    안녕하세요%             
    (base) ➜  CSE 15L git:(＜PA3＞) ✗ cat lecture1/messages/temp.txt
    cat: lecture1/messages/temp.txt: No such file or directory
    (base) ➜  CSE 15L git:(＜PA3＞) ✗ pwd
    /Users/admin/Documents/Documents_Minseo_Chu_MacBook/ucsd_docs/CSE 15L
  </code></pre>
</li>

<blockquote>
  The error prints the content of the file.
  <br> If the isn't a corresponding file, it gives out error: "cat: (inputted path): No such file or directory"
  <br>working directory: <code>/Users/admin/Documents/Documents_Minseo_Chu_MacBook/ucsd_docs/CSE 15L</code>
</blockquote>

</ol>
