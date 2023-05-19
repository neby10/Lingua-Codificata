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
- [PEP8](https://peps.python.org/pep-0008/)
- [Python Cheat Sheet](https://perso.limsi.fr/pointal/_media/python:cours:mementopython3-english.pdf)
- [Regular Expression Cheat Sheet](https://www.dataquest.io/wp-content/uploads/2019/03/python-regular-expressions-cheat-sheet.pdf)
- [Importance of Rounding Appropriately](https://realpython.com/python-rounding/#:~:text=Python%20has%20a%20built%2Din,number%20rounded%20to%20an%20integer.)
- [Regex Details](https://www3.ntu.edu.sg/home/ehchua/programming/howto/Regexe.html)


### Python Web Development Frameworks
- Flask: provides complete control and is ideal for small projects that require experimentation.
- Django: complex framework that requires extensive knowledge, but is one of the best for developing sophisticated applications.

---

## Nitty Gritty

Strings - Python strings are immutable. Instead, you must create a new one.
```
my_string = “Hello, World”
my_string = “J” + my_string[1:]
```


String Methods <br>
**len()** returns the length of a string.

List Methods <br>
**len()** returns the length of a list.


Documentation Strings for Functions <br>
- first line should always be a short, concise summary of the object’s purpose. 
- if there are more lines in the documentation string, the second line should be blank. The following lines should be one or more paragraphs describing the objects calling conventions, side effects, etc.
```
> def my_function():
>> “””Do nothing, but document it.
>>   No, really, it doesn’t do anything.
>> “””
>> pass

> print(my_function.__doc__)
```

Reading Txt Files

The file object provides you with three methods for reading text from a text file:
- **read(size)** – read some contents of a file based on the optional size and return the contents as a string. If you omit the size, the read() method reads from where it left off till the end of the file. If the end of a file has been reached, the read() method returns an empty string.
- **readline()** – read a single line from a text file and return the line as a string. If the end of a file has been reached, the readline() returns an empty string.
- **readlines()** – read all the lines of the text file into a list of strings. This method is useful if you have a small file and you want to manipulate the whole text of that file.

Read File Line by Line:
```
with open('the-zen-of-python.txt') as f:
    for line in f:
        print(line.strip())
```



CSV Files Sample Code
```
import csv
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
            selected_columns = [[row[2], row[6], row[7], row[8] ]
            csv_writer.writerow(selected_columns)
```


JSON Files Sample Code <br>
**json.load()** -> used to read the JSON document from file
```
with open("sample.json", "r") as input_file:
   data = json.load(input_file)
```
**json.loads()** -> used to convert the JSON string document into Python dictionary
```
json_object = '{"name": "John", "age": 30, "city": "New York"}'
data = json.loads(json_object)
```

**json.dump()** -> writes data to the file or other desired location
```
with open("sample2.json", "w") as output_file:
   json.dump(data, output_file)
```


## Working with XML Files: Sample Code <br>
### Working with XML Files: Sample Code <br>
#### Working with XML Files: Sample Code <br>


ElementTree is a built-in Python library for parsing XML.
```
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
```

Output
```
(base) Nicholass-Air:pythonpractice nicholaseby$ python xmlchallenges.py
Gambardella, Matthew
price 44.95 | price 5.95 | price 5.95 | price 5.95 | price 5.95 | price 4.95 | price 4.95 | price 4.95 | price 6.95 | price 36.95 | price 36.95 | price 49.95 |
book bk101 | book bk102 | book bk103 | book bk104 | book bk105 | book bk106 | book bk107 | book bk108 | book bk109 | book bk110 | book bk111 | book bk112 |
```

Create New XML File
```
new_root = ET.Element('new_root')

for child in root:
   if child.tag in 'book':
       new_root.append(child)
  
new_tree = ET.ElementTree(new_root)
new_tree.write("myfilenew.xml")
```