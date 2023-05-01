Download Link: https://assignmentchef.com/product/solved-elen4720-problem-4
<br>
Problem 1 (Markov chains)

In this problem, you will rank 769 college football teams based on the scores of every game in the 2019 season. The data provided in CFB2019scores.csv contains the result of one game on each line in the format

Team A index, Team A points, Team B index, Team B points.

If Team A has more points than Team B, then Team A wins, and vice versa. The index of a team refers to the row of “TeamNames.txt” where that team’s name can be found.

Construct a 769×769 random walk matrix <em>M </em>on the college football teams. First construct the unnormalized matrix <em>M</em><sub>c </sub>with values initialized to zeros. For one particular game, let <em>i </em>be the index of Team A and <em>j </em>the index of Team B. Then update

<em>M</em>c<em>ii </em>← <em>M</em>c<em>ii </em>+ 1{Team A wins} + pointspoints<em>i</em>+points<em>i               j </em><em>,</em>

points<em><sub>j</sub></em>

c                                             {Team B wins} + points<em>i</em>+points<em>j </em><em>,</em>

<em>M</em>c<em>ij </em>← <em>M</em>c<em>ij </em>+ 1{Team B wins} + pointspoints<em>i</em>+points<em>j        j </em><em>, </em>{Team A wins} + pointspoints<em>i</em>+points<em>i      j </em><em>.</em>

After processing all games, let <em>M </em>be the matrix formed by normalizing the rows of <em>M</em><sub>c </sub>so they sum to one. Let <em>w<sub>t </sub></em>be the 1×769 state vector at step <em>t</em>. Set <em>w</em><sub>0 </sub>to the uniform distribution. Therefore, <em>w<sub>t </sub></em>is the marginal distribution on each state after <em>t </em>steps given that the starting state is chosen uniformly at random.

<ol start="10000">

 <li>Use <em>w<sub>t </sub></em>to rank the teams by sorting in decreasing value according to this vector. List the top 25 team names (see accompanying file) and their corresponding values in <em>w<sub>t </sub></em>for <em>t </em>= 10<em>,</em>100<em>,</em>1000<em>,</em>10000.</li>

 <li>We saw that <em>w</em><sub>∞ </sub>is related to the first eigenvector of <em>M<sup>T</sup></em>. That is, we can find <em>w</em><sub>∞ </sub>by getting the first eigenvector and eigenvalue of <em>M<sup>T </sup></em>and post-processing:</li>

</ol>

This is because by convention. Also, we observe that <em>λ</em><sub>1 </sub>= 1 for this specific matrix. Plot k<em>w<sub>t </sub></em>− <em>w</em><sub>∞</sub>k<sub>1 </sub>as a function of <em>t </em>for <em>t </em>= 1<em>,…,</em>10000.

Problem 2 (Nonnegative matrix factorization) – 40 points

In this problem you will factorize an <em>N </em>× <em>M </em>matrix <em>X </em>into a rank-<em>K </em>approximation <em>WH</em>, where <em>W </em>is <em>N </em>× <em>K</em>, <em>H </em>is <em>K </em>× <em>M </em>and all values in the matrices are nonnegative. Each value in <em>W </em>and <em>H </em>can be initialized randomly to a positive number, e.g., from a Uniform(1,2) distribution.

The data to be used for this problem consists of 8447 documents from <em>The New York Times</em>. (See below for how to process the data.) The vocabulary size is 3012 words. You will need to use this data to construct the matrix <em>X</em>, where <em>X<sub>ij </sub></em>is the number of times word <em>i </em>appears in document <em>j</em>. Therefore, <em>X </em>is 3012×8447 and most values in <em>X </em>will equal zero.

<ol>

 <li>Implement and run the NMF algorithm on this data using the <em>divergence penalty</em>. Set the rank to 25 and run for 100 iterations. This corresponds to learning 25 topics. Plot the objective as a function of iteration.</li>

 <li>After running the algorithm, normalize the columns of <em>W </em>so they sum to one. For each column of <em>W</em>, list the 10 words having the largest weight and show the weight. The <em>i</em>th row of <em>W </em>corresponds to the <em>i</em>th word in the “dictionary” provided with the data. Organize these lists in a 5×5</li>

</ol>

Comments about Problem 2:

<ul>

 <li>When dividing, you may get 0/0 = NaN. This will cause the algorithm to return all NaN values. You can add a very small number (e.g., 10<sup>−16</sup>) to the denominator to avoid this.</li>

 <li>Each row in nytdata.txt corresponds to a single document. It gives the index of words appearing in that document and the number of times they appear. It uses the format “idx:cnt” with commas separating each unique word in the document. Any index that doesn’t appear in a row has a count of zero for that word. The vocabulary word corresponding to each index is given in the corresponding row of nytvocab.dat.</li>

</ul>