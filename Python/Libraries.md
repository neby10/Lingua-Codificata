# Python Libraries and Modules Notes

## REQUESTS LIBRARY
The requests library is a popular Python library used for making HTTP requests. Here are some of the most commonly used methods in the requests library:
- **requests.get(url, params=None, \*\*kwargs)**: Sends a GET request to the specified URL and returns a response object.
- **requests.post(url, data=None, json=None, \*\*kwargs)**: Sends a POST request to the specified URL and returns a response object.
- **requests.put(url, data=None, \*\*kwargs)**: Sends a PUT request to the specified URL and returns a response object.
- **requests.delete(url, \*\*kwargs)**: Sends a DELETE request to the specified URL and returns a response object.
- **requests.head(url, \*\*kwargs)**: Sends a HEAD request to the specified URL and returns a response object.
- **requests.patch(url, data=None, \*\*kwargs)**: Sends a PATCH request to the specified URL and returns a response object.
- **requests.options(url, \*\*kwargs)**: Sends an OPTIONS request to the specified URL and returns a response object.

In addition to these methods, there are also several other methods in the requests library for handling cookies, sessions, and authentication, among other things

## OS MODULE
The os module in Python provides a way of interacting with the operating system. Here are some of the common methods used with os module:
- **os.getcwd()**: Returns the current working directory as a string.
- **os.chdir(path)**: Changes the current working directory to the given path.
- **os.listdir(path='.')**: Returns a list of all files and directories in the given path.
- **os.mkdir(path, mode=0o777)**: Creates a directory with the given name and permissions (default is 777).
- **os.makedirs(name, mode=0o777, exist_ok=False)**: Creates a directory and any necessary parent directories. The exist_ok parameter determines if an error should be raised if the directory already exists.
- **os.remove(path)**: Deletes the file with the given path.
- **os.rmdir(path)**: Removes the directory with the given path. The directory must be empty.
- **os.path.join(path, *paths)**: Joins one or more path components (strings) to form a complete path.
- **os.path.exists(path)**: Returns True if the given path exists, False otherwise.
- **os.path.isfile(path)**: Returns True if the given path is a file, False otherwise.
- **os.path.isdir(path)**: Returns True if the given path is a directory, False otherwise.
- And many more...

## RE LIBRARY
The re module in Python provides several methods for working with regular expressions. Here are some of the commonly used methods:
- **re.search(pattern, string, flags=0)**: Searches the string for the first occurrence of the pattern and returns a match object if found. Returns None if no match is found.
- **re.match(pattern, string, flags=0)**: Matches the pattern against the beginning of the string and returns a match object if found. Returns None if no match is found.
- **re.findall(pattern, string, flags=0)**: Searches the string for all occurrences of the pattern and returns a list of all matches.
- **re.sub(pattern, repl, string, count=0, flags=0)**: Substitutes all occurrences of the pattern in the string with the replacement string repl.
- **re.split(pattern, string, maxsplit=0, flags=0)**: Splits the string at the occurrences of the pattern and returns a list of the resulting substrings.
- **re.compile(pattern, flags=0)**: Compiles the regular expression pattern into a regular expression object that can be used with other re module methods.
- **match.group(\[group1, ...])**: Returns one or more subgroups of the match. If no arguments are passed, returns the entire match.
- **match.start(\[group])**: Returns the starting position of the match or the specified group.
- **match.end(\[group])**: Returns the ending position of the match or the specified group.
- **match.span(\[group])**: Returns a tuple containing the starting and ending positions of the match or the specified group.
- **re.IGNORECASE** or **re.I**: Makes the pattern case-insensitive.
- **re.MULTILINE** or **re.M**: Allows the ^ and $ characters to match the beginning and end of each line, instead of just the beginning and end of the entire string.
- And many more...

## MatPlotLib LIBRARY
The matplotlib library provides a wide range of functions to create and customize various types of plots, charts, and graphs. Some of the commonly used methods in matplotlib include:
- **plot()**: This method is used to create line plots.
- **scatter()**: This method is used to create scatter plots.
- **bar()**: This method is used to create bar charts.
- **hist()**: This method is used to create histograms.
- **pie()**: This method is used to create pie charts.
- **imshow()**: This method is used to display image data.
- **subplots()**: This method is used to create multiple plots on the same figure.
- **xlabel()**: This method is used to set the label for the x-axis.
- **ylabel()**: This method is used to set the label for the y-axis.
- **title()**: This method is used to set the title for the plot.
- **legend()**: This method is used to display the legend for the plot.
- **grid()**: This method is used to display grid lines on the plot.
- **savefig()**: This method is used to save the plot as an image file.
These are just a few examples of the many methods available in matplotlib. The library is quite extensive and provides a lot of flexibility to create and customize plots to suit different needs.

```
import matplotlib.pyplot as plt

\# Create a figure containing a single axes
fig, ax = plt.subplots() # subplots returns a tuple containing the Figure and Axes objects

\# Plot data
ax.plot([0, 1, 2, 3, 4], [0, 5, 8, 2, 3])

\# Show the graph through terminal
plt.show()
```

## Beautiful Soup
The Python Beautiful Soup library provides several methods to parse and extract data from HTML and XML documents. Some of the most commonly used methods include:
- **BeautifulSoup()**: This method is used to parse the HTML or XML document and create a BeautifulSoup object. It takes two arguments: the document itself, and the parser to use.
- **find()**: This method is used to search for the first occurrence of a particular tag in the document. It takes a tag name as an argument.
- **find_all()**: This method is used to find all occurrences of a particular tag in the document. It takes a tag name as an argument.
- **select()**: This method is used to find all occurrences of a particular CSS selector in the document. It takes a CSS selector as an argument.
- **get_text()**: This method is used to extract the text content of a tag.
- **attrs()**: This method is used to extract the attributes of a tag as a dictionary.
- **prettify()**: This method is used to display the document in a formatted way.
- **replace_with()**: This method is used to replace a tag with a new tag or string.
- **extract()**: This method is used to remove a tag from the document.

Beautiful Soup is a Python library for web scraping that allows you to parse HTML and XML documents in an efficient manner. 
from bs4 import BeautifulSoup

```
\# open html file and read contents
with open("sample.html", "r") as file:
    contents = file.read()

\# creates a new BeautifulSoup object that can then be parsed using .find(), .prettify(), .find_all(), .get_text()
soup = BeautifulSoup(contents, 'html.parser')
print(soup.find_all('p'))
```