# NLP_Project_2
Evaluating Hawkishness and Dovishness of FOMC Meeting Minutes

My project aimed to investigate the impact of the Federal Reserve's hawkish or dovish statements on the economy. In this comprehensive analysis, I utilized Natural Language Processing (NLP) techniques to evaluate the tone of the Federal Reserve's Press Release statements and transcripts of conferences, specifically focusing on determining how hawkish or dovish these communications were.
The documents that I analyzed were the Press Release statements and the transcripts of the Press Conferences, held by the Federal Reserve. The list of these documents is found in this website:
* https://www.federalreserve.gov/monetarypolicy/fomccalendars.htm

I processed these documents using Python. The Press Release statements were directly obtained from the web, so they were processed as HTML documents. The Press Conference transcripts were stored as PDF files. I used a Python package to read them, clean the text, and store them in TXT files.
Then, I had to assign scores to determine how hawkish or dovish the documents were. The scores were determined using FinBERT.
* https://github.com/gtfintechlab/fomc-hawkish-dovish/tree/main

FinBERT analyses each sentence and assigns a label. To quantify the level of hawkishness or dovishness in these statements, I assigned numerical scores: a more positive score indicated a hawkish tone, while a more negative score indicated a dovish one. The score was made by adding the number of hawkish sentences and subtracting the number of dovish sentences. Neutral sentences were not considered.
Given that the Press Conference transcripts had a higher number of sentences than the Press Release statements, the latter had greater scores. Therefore, I took a weighted average where I assigned more weight to the score of the Press Release statements.
This scoring system allowed me to quantitatively measure the sentiment and policy stance conveyed by the Federal Reserve in its communications. We can see that during the pandemic, the FED became more dovish, and in the subsequent years of inflation, more hawkish.

In addition to analyzing the textual data, I collected financial data related to the 2-year and 10-year yield spreads for U.S. treasuries. This data included the percentage change in these spreads on both the day before and at the end of the day when the Federal Reserve's statements were released. I also considered the percentage changes for the 2-year and 10-year yields independently.
* US 10-Year Constant Maturity Yields (Daily): https://fred.stlouisfed.org/series/DGS10
* US 2-Year Constant Maturity Yields (Daily): https://fred.stlouisfed.org/series/DGS2

The core of my analysis involved examining the relationships between the calculated scores for hawkishness-dovishness and the financial data. My findings showed positive correlations between the scores and the financial metrics, suggesting a connection between the Federal Reserve's tone and market behavior. In particular, I noted a significant correlation of 0.3 between the scores and the 2-year-10-year yield spread, which implies that there is a positive association. This result indicates that when the Federal Reserve's statements were more hawkish, it had a positive influence on the yield spread, and vice versa.

Correlation table:
| | Spread percent change | 2-yr percent change | 10-yr percent change |
| -------- | -------- | -------- | -------- |
|   Score   |   0.317493   |   0.130166   |   0.151796   |

Overall, my project provided valuable insights into the interplay between central bank communications and financial markets, demonstrating that NLP techniques can be effectively employed to measure sentiment and gauge their potential impacts on economic indicators and market behavior. My work could have significant implications for investors and financial professionals seeking to understand and respond to central bank policies and their associated market movements.

