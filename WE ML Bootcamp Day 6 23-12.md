EDA & Pandas & Matplotlib tutorial: https://colab.research.google.com/drive/1WPhsuuTmnnFwUAIRKlpdHLQF56WOmFNP#scrollTo=FCcJhrulV7qz&uniqifier=1

- Dataframe = 2d, series = 1d
- The problem with round() function in python and its inability to represent numbers that don't have terminating base 2 expansion: https://docs.python.org/3/tutorial/floatingpoint.html#tut-fp-issues (gist: if they can't be represented in binary fractions)
- Matplotlib originated to provide graphics for MATLAB users, and later developed a pythonic way of usage

- Seaborn = wrapper on Matplotlib
- Bokeh = more interactive and web-based capabilities https://docs.bokeh.org/en/latest/docs/gallery.html
- Plotly = has a flask framework and also interactive
- Vega Altair = declarative = functional = Haskellish (lesser lines of code) 
- Testing can only show presence of mistakes, it cannot show if code has mistakes


Sources to read research paper: Academia, Elsevier, 


## Chat AI discussion:
- EliZa = based on non directive psychotherapy (Rogerian)
- MIT students didn't want to make the conversations global because they confided in EliZa
- https://cacm.acm.org/blogs/blog-cacm/268103-what-do-chatgpt-and-ai-based-automatic-program-generation-mean-for-the-future-of-software/fulltext Article confused OOP Software legend Bertrand Mayer into believing the merits of AI
- Companies sell products that confidently sell bullshit since humans psyche is vulnerable to easy delusions
- Our modern society me bullshit sells

- Ensure you have an auditable trait for every work you do, so no one accuses you of plagiarism.

## Scripting

Q. Rearrange the columns in a 2 column file using Linux shell
cut -f1 $l >/tmp/a
cut -f2 $l >/tmp/a
paste /tmp/b /tmp/a > $l.reverse

- Piping: cascading outputs of 1 command as input to another
- cut -d will also delete it from orig file
- tr -d "\\"" will remove the quotes (just 1 slash)
- ``grep -v "^ *$"  ``
this removed the special chars other than words from the output

- ``tr "[A-Z]" "[a-z]" < WarAndPeace.txt| tr -c "[a-z0-9]" "\n" |grep -v "^ *$" | sort | uniq -c | sort -nr |head``
this whole command is used to display the top 10 most freq (sorted by nr numeric reverse) unique (uniq) words

- Basic definitions:
	- $ = anchors a pattern to the end of line
	- grep = it filters lines that matches pattern (gives lines that match) (global regular expression print)
	- -v = invert (get inverse of result)
	- uniq = assumes things are sorted, if successive repeat then remove
	- sort -nr = n means numerically, r means reverse (descending) (2 before 1100)
	- head = top 10
	- tr = 1:1 translation of input to output `tr "[A-Z]" "[a-z]" < num.txt > num1.text`
	- less = a pager, displays contents one page at a time

# How to not be scared of coding
- Try to use unix command line instead of windows for coding, it'll improve the coding skills
- https://en.wikipedia.org/wiki/Computer_programming_in_the_punched_card_era they used to code programs in punched lines and compile it only once a day.
- Think through the logic first, don't compile/run the program just build your logic
- Computer programming will be difficult when you see the error message, don't read it and find it stressful to run the messages
- An error is just telling you what to do next, and it is an intellectual challenge

# Resources:
- Python for Data Analysis by Wes Mckinney (person behind pandas creation)
- Thinking like a Feminist - Nivedita Menon