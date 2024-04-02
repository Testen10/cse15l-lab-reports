# Week 1 Lab Report
## cd
<ol>
<li><p> Command with no arguments </p>
  <pre><code>
    (base) ➜  lecture1 git:(main) ✗ cd
    (base) ➜  ~ git:(＜PA3＞) ✗ pwd
    /Users/admin
  </code></pre>
</li>
  
  changes the current directory to `User/admin` folder
 <br>working directory: `User/admin` 

<li><p> Command with path to a directory as an argument </p>
  <pre><code>
    (base) ➜  CSE 15L git:(＜PA3＞) ✗ cd lecture1                                                               
    (base) ➜  lecture1 git:(main) ✗ pwd
    /Users/admin/Documents/Documents_Minseo_Chu_MacBook/ucsd_docs/CSE 15L/lecture1
  </code></pre>
</li>

  changes the current directory to the inputted directory path
  <br>working directory: `/Users/admin/Documents/Documents_Minseo_Chu_MacBook/ucsd_docs/CSE 15L/lecture1`

<li><p> Command with path to a file as an argument </p>
  <pre><code>
    (base) ➜  lecture1 git:(main) ✗ cd '/Users/admin/Documents/Documents_Minseo_Chu_MacBook/ucsd_docs/CSE 15L/Hello.java'
    cd: not a directory: /Users/admin/Documents/Documents_Minseo_Chu_MacBook/ucsd_docs/CSE 15L/Hello.java
  </code></pre>
</li>

  prints out error message since file is not a directory
  <br>working directory: `/Users/admin/Documents/Documents_Minseo_Chu_MacBook/ucsd_docs/CSE 15L/lecture1`
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

  prints the list of files in the current directory
  <br>working directory: `/Users/admin/Documents/Documents_Minseo_Chu_MacBook/ucsd_docs/CSE 15L`
  
<li><p> Command with path to a directory as an argument </p>
  <pre><code>
    (base) ➜  CSE 15L git:(＜PA3＞) ✗ ls lecture1
    README   messages
    (base) ➜  CSE 15L git:(＜PA3＞) ✗ pwd
    /Users/admin/Documents/Documents_Minseo_Chu_MacBook/ucsd_docs/CSE 15L
  </code></pre>
</li>

  prints the list of files in the directory referring to the inputted directory path, but doesn't change the working directory
  <br>working directory: `/Users/admin/Documents/Documents_Minseo_Chu_MacBook/ucsd_docs/CSE 15L`
  
<li><p> Command with path to a file as an argument </p>
  <pre><code>
    (base) ➜  CSE 15L git:(＜PA3＞) ✗ ls Hello.java
    Hello.java
    (base) ➜  CSE 15L git:(＜PA3＞) ✗ pwd
    /Users/admin/Documents/Documents_Minseo_Chu_MacBook/ucsd_docs/CSE 15L
  </code></pre>
</li>

  prints the name of file in the inputted path, but doesn't change the working directory
  <br>working directory: `/Users/admin/Documents/Documents_Minseo_Chu_MacBook/ucsd_docs/CSE 15L`

</ol>
