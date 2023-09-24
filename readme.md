# U of T quick facts

- This is a project on scraping an html file with the example of [University of Toronto's quick facts](https://www.utoronto.ca/about-u-of-t/quick-facts). I used jupyter notebook and python code to extract texts, links, figures, words, and to analyze web content.

# How

- First, using such libraries as `pandas`, `numpy`, `urlparse`, `HTMLSession`, I obtained some raw html texts and put them into DataFrames. Then, with `BeautifulSoup`, I extracted info based on how the web page was organized, and obtained texts and figures for further analysis or organization. Specifically, I plotted graphs with `matplotlib` about student populations.

- ![Quick facts](https://www.utoronto.ca/sites/default/files/2023-09/graph-student-enrolment.jpg)

- ![Funds chart](https://www.utoronto.ca/sites/default/files/2023-09/chart-research-funds.png)

- This school has already listed funding as a pie chart. I will make additional analysis on my own.

# Findings

- It is a simple fact sheet about this public university such as its campuses, a breakdown of student populations, and sources of funding. Interestingly, while it is convenient for public viewing, the web page elements were not optimized nor well-organized for convenient scraping. I found that

```
# Find elements containing text data
text_elements = soup.find_all('div', class_='field field--name-field-add-text field--type-string-long field--label-hidden field__item')

# Find elements containing integer data
integer_elements = soup.find_all('div', class_='field field--name-field-add-number field--type-integer field--label-hidden field__item')
```

there was the confusing use of web elements for different sections of quick facts, as if it was written by multiple writers with little coordination.

- St. George was the most popular and populous campus. While the distribution of undergraduates reflected this, the graduate school did not, being dominated by St. George. Because of the nature of this html file, I extracted separate figures on new (undergraduate) students in Fall 2022-2023

```
New undergraduates
9,244 at our St. George Campus
3,644 at our Scarborough Campus
3,321 at our Mississauga Campus
```

```
Undergraduates
46,905 at our St. George Campus
13,957 at our Scarborough Campus
15,199 at our Mississauga Campus
```

for comparison. New undergraduates and the summation of undergraduates show the same trend that a majority of undergraduates were at St. George, and Scarborough and Mississauga had a similar undergraduate population.

- For some reason, United Kingdom and Great Britain were two separate entries of alumni. I fixed that.

- US was home to the second-largest group of alumni, but China will surpass the US soon with the second-largest current student population.

- HK was home to a disproportionate number of alumni.

- Further insights would be helpful for exploring budget files, for instance, in the form of PDF files (`PyPDF2`), as well as scraping graphical information since this project did not scrape much about funding other than a single figure.

# Acknowledgement

- This project is inspired by Will, the instructor, and [Cantek](https://www.cantekcanada.com/).

# Reference

- [Quick facts | University of Toronto](https://www.utoronto.ca/about-u-of-t/quick-facts) (accessed 21 Sep 2023)
