<main class="col-md markdown-body">

<h1 id="plurality">Plurality</h1>

<p>Implement a program that runs a plurality election, per the below.</p>

<div class="highlighter-rouge"><div class="highlight"><pre class="highlight"><code>$ ./plurality Alice Bob Charlie
Number of voters: 4
Vote: Alice
Vote: Bob
Vote: Charlie
Vote: Alice
Alice
</code></pre></div></div>

<h2 id="background">Background</h2>

<p>Elections come in all shapes and sizes. In the UK, the <a href="https://www.parliament.uk/education/about-your-parliament/general-elections/">Prime Minister</a> is officially appointed by the monarch, who generally chooses the leader of the political party that wins the most seats in the House of Commons. The United States uses a multi-step <a href="https://www.archives.gov/federal-register/electoral-college/about.html">Electoral College</a> process where citizens vote on how each state should allocate Electors who then elect the President.</p>

<p>Perhaps the simplest way to hold an election, though, is via a method commonly known as the “plurality vote” (also known as “first-past-the-post” or “winner take all”). In the plurality vote, every voter gets to vote for one candidate. At the end of the election, whichever candidate has the greatest number of votes is declared the winner of the election.</p>

<h2 id="getting-started">Getting Started</h2>

<p>Here’s how to download this problem’s “distribution code” (i.e., starter code) into your own CS50 IDE. Log into <a href="https://ide.cs50.io/">CS50 IDE</a> and then, in a terminal window, execute each of the below.</p>

<ul>
  <li data-marker="*">Execute <code class="highlighter-rouge">cd</code> to ensure that you’re in <code class="highlighter-rouge">~/</code> (i.e., your home directory).</li>
  <li data-marker="*">Execute <code class="highlighter-rouge">mkdir pset3</code> to make (i.e., create) a directory called <code class="highlighter-rouge">pset3</code> in your home directory.</li>
  <li data-marker="*">Execute <code class="highlighter-rouge">cd pset3</code> to change into (i.e., open) that directory.</li>
  <li data-marker="*">Execute <code class="highlighter-rouge">mkdir plurality</code> to make (i.e., create) a directory called <code class="highlighter-rouge">plurality</code> in your <code class="highlighter-rouge">pset3</code> directory.</li>
  <li data-marker="*">Execute <code class="highlighter-rouge">cd plurality</code> to change into (i.e., open) that directory.</li>
  <li data-marker="*">Execute <code class="highlighter-rouge">wget https://cdn.cs50.net/2019/fall/psets/3/plurality/plurality.c</code> to download this problem’s distribution code.</li>
  <li data-marker="*">Execute <code class="highlighter-rouge">ls</code>. You should see this problem’s distribution code, in a file called <code class="highlighter-rouge">plurality.c</code>.</li>
</ul>

<h2 id="understanding">Understanding</h2>

<p>Let’s now take a look at <code class="highlighter-rouge">plurality.c</code> and read through the distribution code that’s been provided to you.</p>

<p>The line <code class="highlighter-rouge">#define MAX 9</code> is some syntax used here to mean that <code class="highlighter-rouge">MAX</code> is a constant (equal to <code class="highlighter-rouge">9</code>) that can be used throughout the program. Here, it represents the maximum number of candidates an election can have.</p>

<p>The file then defines a <code class="highlighter-rouge">struct</code> called a <code class="highlighter-rouge">candidate</code>. Each <code class="highlighter-rouge">candidate</code> has two fields: a <code class="highlighter-rouge">string</code> called <code class="highlighter-rouge">name</code> representing the candidate’s name, and an <code class="highlighter-rouge">int</code> called <code class="highlighter-rouge">votes</code> representing the number of votes the candidate has. Next, the file defines a global array of <code class="highlighter-rouge">candidates</code>, where each element is itself a <code class="highlighter-rouge">candidate</code>.</p>

<p>Now, take a look at the <code class="highlighter-rouge">main</code> function itself. See if you can find where the program sets a global variable <code class="highlighter-rouge">candidate_count</code> representing the number of candidates in the election, copies command-line arguments into the array <code class="highlighter-rouge">candidates</code>, and asks the user to type in the number of voters. Then, the program lets every voter type in a vote (see how?), calling the <code class="highlighter-rouge">vote</code> function on each candidate voted for. Finally, <code class="highlighter-rouge">main</code> makes a call to the <code class="highlighter-rouge">print_winner</code> function to print out the winner (or winners) of the election.</p>

<p>If you look further down in the file, though, you’ll notice that the <code class="highlighter-rouge">vote</code> and <code class="highlighter-rouge">print_winner</code> functions have been left blank. This part is up to you to complete!</p>

<h2 id="specification">Specification</h2>

<p>Complete the implementation of <code class="highlighter-rouge">plurality.c</code> in such a way that the program simulates a plurality vote election.</p>

<ul>
  <li data-marker="*">Complete the <code class="highlighter-rouge">vote</code> function.
    <ul>
      <li data-marker="*"><code class="highlighter-rouge">vote</code> takes a single argument, a <code class="highlighter-rouge">string</code> called <code class="highlighter-rouge">name</code>, representing the name of the candidate who was voted for.</li>
      <li data-marker="*">If <code class="highlighter-rouge">name</code> matches one of the names of the candidates in the election, then update that candidate’s vote total to account for the new vote. The <code class="highlighter-rouge">vote</code> function in this case should return <code class="highlighter-rouge">true</code> to indicate a successful ballot.</li>
      <li data-marker="*">If <code class="highlighter-rouge">name</code> does not match the name of any of the candidates in the election, no vote totals should change, and the <code class="highlighter-rouge">vote</code> function should return <code class="highlighter-rouge">false</code> to indicate an invalid ballot.</li>
      <li data-marker="*">You may assume that no two candidates will have the same name.</li>
    </ul>
  </li>
  <li data-marker="*">Complete the <code class="highlighter-rouge">print_winner</code> function.
    <ul>
      <li data-marker="*">The function should print out the name of the candidate who received the most votes in the election, and then print a newline.</li>
      <li data-marker="*">It is possible that the election could end in a tie if multiple candidates each have the maximum number of votes. In that case, you should output the names of each of the winning candidates, each on a separate line.</li>
    </ul>
  </li>
</ul>

<p>You should not modify anything else in <code class="highlighter-rouge">plurality.c</code> other than the implementations of the <code class="highlighter-rouge">vote</code> and <code class="highlighter-rouge">print_winner</code> functions (and the inclusion of additional header files, if you’d like).</p>

<h2 id="usage">Usage</h2>

<p>Your program should behave per the examples below.</p>

<div class="highlighter-rouge"><div class="highlight"><pre class="highlight"><code>$ ./plurality Alice Bob
Number of voters: 3
Vote: Alice
Vote: Bob
Vote: Alice
Alice
</code></pre></div></div>

<div class="highlighter-rouge"><div class="highlight"><pre class="highlight"><code>$ ./plurality Alice Bob
Number of voters: 3
Vote: Alice
Vote: Charlie
Invalid vote.
Vote: Alice
Alice
</code></pre></div></div>

<div class="highlighter-rouge"><div class="highlight"><pre class="highlight"><code>$ ./plurality Alice Bob Charlie
Number of voters: 5
Vote: Alice
Vote: Charlie
Vote: Bob
Vote: Bob
Vote: Alice
Alice
Bob
</code></pre></div></div>

<h2 id="testing">Testing</h2>

<p>Be sure to test your code to make sure it handles…</p>

<ul>
  <li data-marker="*">An election with any number of candidate (up to the <code class="highlighter-rouge">MAX</code> of <code class="highlighter-rouge">9</code>)</li>
  <li data-marker="*">Voting for a candidate by name</li>
  <li data-marker="*">Invalid votes for candidates who are not on the ballot</li>
  <li data-marker="*">Printing the winner of the election if there is only one</li>
  <li data-marker="*">Printing the winner of the election if there are multiple winners</li>
</ul>

<p>Execute the below to evaluate the correctness of your code using <code class="highlighter-rouge">check50</code>. But be sure to compile and test it yourself as well!</p>

<div class="highlighter-rouge"><div class="highlight"><pre class="highlight"><code>check50 cs50/problems/2020/x/plurality
</code></pre></div></div>

<p>Execute the below to evaluate the style of your code using <code class="highlighter-rouge">style50</code>.</p>

<div class="highlighter-rouge"><div class="highlight"><pre class="highlight"><code>style50 plurality.c
</code></pre></div></div>

<h2 id="how-to-submit">How to Submit</h2>

<p>Execute the below, logging in with your GitHub username and password when prompted. For security, you’ll see asterisks (<code class="highlighter-rouge">*</code>) instead of the actual characters in your password.</p>

<div class="highlighter-rouge"><div class="highlight"><pre class="highlight"><code>submit50 cs50/problems/2020/x/plurality
</code></pre></div></div>


</main>
