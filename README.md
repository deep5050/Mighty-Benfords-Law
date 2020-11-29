<div align=center>
  <img align=center src="./logo.svg" alt="logo">
  <br> </br>
 <img align=center src="./intro.svg" alt="intro">
</div>



## INTRODUCTION

In the year 1938, a physicist named Frank Benford published a paper with a law that states that 

> "In many naturally occuring collections of numbers, the first digit is likely to be small. As a matter of fact, the number 1 appears as the leading significant digit in about 30% of the whole collection, while 9 appears as the leading significant digit in about less than 5%".

For example, if you collect a set of numbers, then, according to Benford's Law, 30.1% of those numbers have 1 as their leading significant digit, 17.6% of those number have 2 as their leading signifcant digit and so on. The graph and the table below shows the Benford Curve stating the distribution

![Alt text](https://github.com/sjaishanker/Benford-Analysis-For-Fraud-Detection/blob/master/doc_snippets/Benford_Distribution.png?raw=true)
![Alt text](https://github.com/sjaishanker/Benford-Analysis-For-Fraud-Detection/blob/master/doc_snippets/Table.png?raw=true)

There were rumouirs that some Tax Agencies used Benford's Law to detect fraud activity in user accounts. They would take all the tax invoices and apply benford's law on the set of numbers(basically the tax payment done by individual users) and if the numbers doesnt add up to the benford distribution, then, that person would be in trouble. Obviously, neither the agencies aggreed to this usage of methodology nor did they decline. But this law became a state-of-the-art workflow to detect fraud in any domain that had numbers involved. 

Numbers written on the front page of the newspaper(date, number of people killed, etc) were collected and evaluated into this algorithm and the results were shocking. The number set followed ***Benford's Law distribution***. When I came to know about it, I couldnt believe it. What I had were some facts written in words and my mind cannot accept anything unless there is an implementation proving the law, on realtime data. Therefore, I performed certain analysis based on different types of realtime data to see whether Benford's Law was true or was it just ancient.

