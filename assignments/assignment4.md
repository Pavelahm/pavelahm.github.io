<!DOCTYPE html>
<html>
<head>
    <title>Assignment 4 - Text Analytics using Quanteda</title>
</head>

<body>

<h1>Assignment 4: Text Analytics using Quanteda</h1>

<h2>1. Introduction</h2>
<p>
This assignment applies the quanteda package in R to perform text analytics on US presidential inaugural speeches and Department of Defense (DOD) reports.
</p>

<h2>2. Analysis of Inaugural Speeches</h2>

<h3>Top Words</h3>
<table border="1">
<tr><th>Rank</th><th>Word</th><th>Frequency</th></tr>
<tr><td>1</td><td>freedom</td><td>42</td></tr>
<tr><td>2</td><td>liberty</td><td>25</td></tr>
<tr><td>3</td><td>democracy</td><td>16</td></tr>
</table>

<h3>Key Insights</h3>
<ul>
<li>Focus on democratic values</li>
<li>Strong emphasis on unity</li>
<li>Different rhetorical styles across presidents</li>
</ul>

<h2>3. Wordfish Method</h2>
<p>
Wordfish is an unsupervised method used to estimate document positions based on word frequencies.
</p>

<h2>4. Results</h2>

<table border="1">
<tr><th>President</th><th>Year</th><th>Theta</th></tr>
<tr><td>Trump</td><td>2017</td><td>-1.323</td></tr>
<tr><td>Biden</td><td>2021</td><td>-0.080</td></tr>
<tr><td>Bush</td><td>2005</td><td>1.073</td></tr>
</table>

<h2>5. Interpretation</h2>
<ul>
<li>Trump → negative (populist style)</li>
<li>Bush → positive (traditional style)</li>
<li>Biden → moderate</li>
</ul>

<h2>6. DOD Reports</h2>

<h3>Top Words</h3>
<ul>
<li>operations</li>
<li>defense</li>
<li>capabilities</li>
</ul>

<h3>Insights</h3>
<ul>
<li>Technical and operational focus</li>
<li>Increasingly hawkish trend</li>
</ul>

<h2>7. Conclusion</h2>
<p>
Wordfish successfully captures differences in rhetoric across political and defense documents.
</p>

</body>
</html>
