# My Python Notes

## About Python:
- General Purpose
- High-Level
- Interpreted
- Object-Oriented
- Dynamic Semantics
- Great for both for application development as well as scripting
- Features: dynamic typing, dynamic binding, high-level data structures, modules and packages

## The Zen of Python
Beautiful is better than ugly.
Explicit is better than implicit.
Simple is better than complex.
Complex is better than complicated. Flat is better than nested. Sparse is better than dense.
Readability counts.
Special cases aren't special enough to break the rules.
Although practicality beats purity.
Errors should never pass silently.
Unless explicitly silenced.
In the face of ambiguity, refuse the temptation to guess.
There should be one-- and preferably only one --obvious way to do it.
Although that way may not be obvious at first unless you're Dutch.
Now is better than never.
Although never is often better than *right* now.
If the implementation is hard to explain, it's a bad idea.
If the implementation is easy to explain, it may be a good idea.
Namespaces are one honking great idea -- let's do more of those!

## Naming Conventions
| Type | Naming Convention | Examples |
| ---- | ----------------- | -------- |
| Function | Use a lowercase word or words. Separate words by underscores to improve readability. | function, my_function |
| Variable | Use a lowercase single letter, word, or words. Separate words with underscores to improve readability. | x, var, my_variable |
| Class | Start each word with a capital letter. Do not separate words with underscores. This style is called camel case or pascal case. | Model, MyClass |
| Method | Use a lowercase word or words. Separate words with underscores to improve readability. | class_method, method |
| Constant | Use an uppercase single letter, word, or words. Separate words with underscores to improve readability. | CONSTANT, MY_CONSTANT, MY_LONG_CONSTANT |
| Module | Use a short, lowercase word or words. Separate words with underscores to improve readability. | module.py, my_module.py |
| Package | Use a short, lowercase word or words. Do not separate words with underscores. | package, mypackage |

## Special Notes
- The python interpreter is usually installed as /usr/local/bin/python3.11
- quit() will exit the python interpreter or press control-z

## Python Links

[PEP8](https://peps.python.org/pep-0008/)
[Python Cheat Sheet](https://perso.limsi.fr/pointal/_media/python:cours:mementopython3-english.pdf)
[Regular Expression Cheat Sheet](https://www.dataquest.io/wp-content/uploads/2019/03/python-regular-expressions-cheat-sheet.pdf)
[Importance of Rounding Appropriately](https://realpython.com/python-rounding/#:~:text=Python%20has%20a%20built%2Din,number%20rounded%20to%20an%20integer.)
[Regex Details](https://www3.ntu.edu.sg/home/ehchua/programming/howto/Regexe.html)


---

## Nitty Gritty

Strings - Python strings are immutable. Instead, you must create a new one.
> my_string = “Hello, World”
> my_string = “J” + my_string[1:]


String Methods
len() returns the length of a string.

List Methods
len() returns the length of a list.


Documentation Strings for Functions
-first line should always be a short, concise summary of the object’s purpose. 
-if there are more lines in the documentation string, the second line should be blank. The following lines should be one or more paragraphs describing the objects calling conventions, side effects, etc.
> def my_function():
>> “””Do nothing, but document it.
>>
>>   No, really, it doesn’t do anything.
>>	“””
>>	pass
> 
> print(my_function.__doc__)

Reading Txt Files
The file object provides you with three methods for reading text from a text file:
read(size) – read some contents of a file based on the optional size and return the contents as a string. If you omit the size, the read() method reads from where it left off till the end of the file. If the end of a file has been reached, the read() method returns an empty string.
readline() – read a single line from a text file and return the line as a string. If the end of a file has been reached, the readline() returns an empty string.
readlines() – read all the lines of the text file into a list of strings. This method is useful if you have a small file and you want to manipulate the whole text of that file.
Read File Line by Line:
with open('the-zen-of-python.txt') as f:
    for line in f:
        print(line.strip())


csv files sample code
import csv


print("Welcome to CSV Program\n")


with open("hundredthousand.csv", "r") as file:
   # create a CSV reader object
   csv_reader = csv.reader(file)


   # skip header
   next(csv_reader)


   # set to desired column
   column = 8


   # creates a list of all column values
   num_employees_list = [int(row[column]) for row in csv_reader]


   print("CSV STATISTICS")
   print(f"Average Employees: {sum(num_employees_list) / len(num_employees_list)}")
   print(f"Maximum Employees: {max(num_employees_list)}")
   print(f"Minimum Employees: {min(num_employees_list)}")

#  Create a new csv file using only selected columns


with open("hundredthousand.csv", "r") as input_file:
   # create reader object
   csv_reader = csv.reader(input_file)


   with open("test1.csv", "w") as output_file:
       # create writer object
       csv_writer = csv.writer(output_file)


       # iterate over each item to write to csv
       for row in csv_reader:
           selected_columns = [row[2], row[6], row[7], row[8]]
           csv_writer.writerow(selected_columns)


json files sample code
json.load() -> used to read the JSON document from file
with open("sample.json", "r") as input_file:
   data = json.load(input_file)
json.loads() -> used to convert the JSON string document into Python dictionary
json_object = '{"name": "John", "age": 30, "city": "New York"}'
data = json.loads(json_object)
json.dump() -> writes data to the file or other desired location
with open("sample2.json", "w") as output_file:
   json.dump(data, output_file)



Working with XML Files: Sample Code
ElementTree is a built-in Python library for parsing XML.
print("Welcome to XML Challenges Program\n")


import xml.etree.ElementTree as ET


# parse the XML file, .parse() returns an ElementTree object that can be used to access XML data
tree = ET.parse("myfile.xml")


# get root element
root = tree.getroot()


# .find() searches for the first occurrence of a tag among the immediate children of the current element
# .text returns the text content of an element
my_book = root.find('book')
first_author = my_book.find('author')
print(first_author.text)


# .findall() returns a list of all elements with a given tag name among the immediate children of the current element
for book in root.findall('book'):
   price = book.find('price')
   print(price.tag, price.text, end=" | ")
print()


# .get() returns the value of an attribute with a given name
for book in root.findall('book'):
   my_id = book.get('id')
   print(book.tag, my_id, end=" | ")
print()
Output
(base) Nicholass-Air:pythonpractice nicholaseby$ python xmlchallenges.py
Welcome to XML Challenges Program


Gambardella, Matthew
price 44.95 | price 5.95 | price 5.95 | price 5.95 | price 5.95 | price 4.95 | price 4.95 | price 4.95 | price 6.95 | price 36.95 | price 36.95 | price 49.95 |
book bk101 | book bk102 | book bk103 | book bk104 | book bk105 | book bk106 | book bk107 | book bk108 | book bk109 | book bk110 | book bk111 | book bk112 |

Create New XML File
new_root = ET.Element('new_root')


for child in root:
   if child.tag in 'book':
       new_root.append(child)
  
new_tree = ET.ElementTree(new_root)
new_tree.write("myfilenew.xml")



Beautiful Soup

The Python Beautiful Soup library provides several methods to parse and extract data from HTML and XML documents. Some of the most commonly used methods include:
BeautifulSoup: This method is used to parse the HTML or XML document and create a BeautifulSoup object. It takes two arguments: the document itself, and the parser to use.
find: This method is used to search for the first occurrence of a particular tag in the document. It takes a tag name as an argument.
find_all: This method is used to find all occurrences of a particular tag in the document. It takes a tag name as an argument.
select: This method is used to find all occurrences of a particular CSS selector in the document. It takes a CSS selector as an argument.
get_text: This method is used to extract the text content of a tag.
attrs: This method is used to extract the attributes of a tag as a dictionary.
prettify: This method is used to display the document in a formatted way.
replace_with: This method is used to replace a tag with a new tag or string.
extract: This method is used to remove a tag from the document.

Beautiful Soup is a Python library for web scraping that allows you to parse HTML and XML documents in an efficient manner. 
from bs4 import BeautifulSoup


# open html file and read contents
with open("sample.html", "r") as file:
   contents = file.read()


   # creates a new BeautifulSoup object that can then be parsed using .find(), .prettify(), .find_all(), .get_text()
   soup = BeautifulSoup(contents, 'html.parser')
   print(soup.find_all('p'))



MatPlotLib LIBRARY
The matplotlib library provides a wide range of functions to create and customize various types of plots, charts, and graphs. Some of the commonly used methods in matplotlib include:
plot(): This method is used to create line plots.
scatter(): This method is used to create scatter plots.
bar(): This method is used to create bar charts.
hist(): This method is used to create histograms.
pie(): This method is used to create pie charts.
imshow(): This method is used to display image data.
subplots(): This method is used to create multiple plots on the same figure.
xlabel(): This method is used to set the label for the x-axis.
ylabel(): This method is used to set the label for the y-axis.
title(): This method is used to set the title for the plot.
legend(): This method is used to display the legend for the plot.
grid(): This method is used to display grid lines on the plot.
savefig(): This method is used to save the plot as an image file.
These are just a few examples of the many methods available in matplotlib. The library is quite extensive and provides a lot of flexibility to create and customize plots to suit different needs.
import matplotlib.pyplot as plt


# Create a figure containing a single axes
fig, ax = plt.subplots() # subplots returns a tuple containing the Figure and Axes objects


# Plot data
ax.plot([0, 1, 2, 3, 4], [0, 5, 8, 2, 3])


# Show the graph through terminal
plt.show()


RE LIBRARY
The re module in Python provides several methods for working with regular expressions. Here are some of the commonly used methods:
re.search(pattern, string, flags=0): Searches the string for the first occurrence of the pattern and returns a match object if found. Returns None if no match is found.
re.match(pattern, string, flags=0): Matches the pattern against the beginning of the string and returns a match object if found. Returns None if no match is found.
re.findall(pattern, string, flags=0): Searches the string for all occurrences of the pattern and returns a list of all matches.
re.sub(pattern, repl, string, count=0, flags=0): Substitutes all occurrences of the pattern in the string with the replacement string repl.
re.split(pattern, string, maxsplit=0, flags=0): Splits the string at the occurrences of the pattern and returns a list of the resulting substrings.
re.compile(pattern, flags=0): Compiles the regular expression pattern into a regular expression object that can be used with other re module methods.
match.group([group1, ...]): Returns one or more subgroups of the match. If no arguments are passed, returns the entire match.
match.start([group]): Returns the starting position of the match or the specified group.
match.end([group]): Returns the ending position of the match or the specified group.
match.span([group]): Returns a tuple containing the starting and ending positions of the match or the specified group.
re.IGNORECASE or re.I: Makes the pattern case-insensitive.
re.MULTILINE or re.M: Allows the ^ and $ characters to match the beginning and end of each line, instead of just the beginning and end of the entire string.
These are just a few of the methods and flags available in the re module. There are many more options for customizing and fine-tuning regular expression searches in Python.

OS MODULE
The os module in Python provides a way of interacting with the operating system. Here are some of the common methods used with os module:
os.getcwd(): Returns the current working directory as a string.
os.chdir(path): Changes the current working directory to the given path.
os.listdir(path='.'): Returns a list of all files and directories in the given path.
os.mkdir(path, mode=0o777): Creates a directory with the given name and permissions (default is 777).
os.makedirs(name, mode=0o777, exist_ok=False): Creates a directory and any necessary parent directories. The exist_ok parameter determines if an error should be raised if the directory already exists.
os.remove(path): Deletes the file with the given path.
os.rmdir(path): Removes the directory with the given path. The directory must be empty.
os.path.join(path, *paths): Joins one or more path components (strings) to form a complete path.
os.path.exists(path): Returns True if the given path exists, False otherwise.
os.path.isfile(path): Returns True if the given path is a file, False otherwise.
os.path.isdir(path): Returns True if the given path is a directory, False otherwise.
These are just a few of the many methods provided by the os module.


REQUESTS LIBRARY

The requests library is a popular Python library used for making HTTP requests. Here are some of the most commonly used methods in the requests library:
requests.get(url, params=None, **kwargs): Sends a GET request to the specified URL and returns a response object.
requests.post(url, data=None, json=None, **kwargs): Sends a POST request to the specified URL and returns a response object.
requests.put(url, data=None, **kwargs): Sends a PUT request to the specified URL and returns a response object.
requests.delete(url, **kwargs): Sends a DELETE request to the specified URL and returns a response object.
requests.head(url, **kwargs): Sends a HEAD request to the specified URL and returns a response object.
requests.patch(url, data=None, **kwargs): Sends a PATCH request to the specified URL and returns a response object.
requests.options(url, **kwargs): Sends an OPTIONS request to the specified URL and returns a response object.
In addition to these methods, there are also several other methods in the requests library for handling cookies, sessions, and authentication, among other things



Python Web Development Frameworks
Flask provides complete control and is ideal for small projects that require experimentation. Django is a complex framework that requires extensive knowledge, but is one of the best for developing sophisticated applications.
