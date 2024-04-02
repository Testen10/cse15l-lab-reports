# Week 1 Lab Report
## cd
<p> Command with no arguments </p>
  <pre><code>
    (base) ➜  lecture1 git:(main) ✗ cd
    (base) ➜  ~ git:(＜PA3＞) ✗
  </code></pre>
  
<p> Command with path to a directory as an argument </p>
  <pre><code>
    (base) ➜  ~ git:(＜PA3＞) ✗ cd '/Users/admin/Documents/Documents_Minseo_Chu_MacBook/ucsd_docs/CSE 15L/lecture1'
    (base) ➜  lecture1 git:(main) ✗ 
  </code></pre>

<p> Command with path to a file as an argument </p>
  <pre><code>
    (base) ➜  lecture1 git:(main) ✗ cd '/Users/admin/Documents/Documents_Minseo_Chu_MacBook/ucsd_docs/CSE 15L/Hello.java'
    cd: not a directory: /Users/admin/Documents/Documents_Minseo_Chu_MacBook/ucsd_docs/CSE 15L/Hello.java
  </code></pre>

## ls
<ol>
<li><p> Command with no arguments </p>
  <pre><code>
    ((base) ➜  CSE 15L git:(＜PA3＞) ✗ ls 
    Hello.class Hello.java  lecture1    test.java
  </code></pre>
</li>
  
<li><p> Command with path to a directory as an argument </p>
  <pre><code>
    (base) ➜  CSE 15L git:(＜PA3＞) ✗ ls lecture1
    README   messages
  </code></pre>
</li>
  
<li><p> Command with path to a file as an argument </p>
  <pre><code>
    (base) ➜  CSE 15L git:(＜PA3＞) ✗ ls Hello.java
    Hello.java
  </code></pre>
</li>

</ol>
  
For each of the commands cd, ls, and cat, and using the workspace you created in this lab:

Share an example of using the command with no arguments.
Share an example of using the command with a path to a directory as an argument.
Share an example of using the command with a path to a file as an argument.
So that's 9 total examples (3 for each command). For each of the 9 examples, include:

A screenshot or Markdown code block showing the command and its output.
What the absolute path to the working directory was when the command was run.
A sentence or two explaining why you got that output (e.g. what was in the filesystem, what it meant to have no arguments).
Indicate explicitly whether the output is an error or not, and if it's an error, explain why it's an error in one or two sentences. Note: Make sure to use backticks ` around keywords such as commands, file names, paths, etc. to make them show up as code like cd.
You will upload your submission by publishing the page on Github Pages, then printing the page to PDF and uploading to the Lab Report 1 assignment on Gradescope.

