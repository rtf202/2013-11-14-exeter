
# Data handling in Python

First, lets start python. We will do everything using ipython, which provides a nice interactive python shell. We start ipython using the command

    $ ipython

Writing a program involves creating and manipulating data, which are held in variables. For example, you have probably used strings and numbers, for example

    $ a = 42
    $ b = 65
    $ a + b
    107

prints out 107. Equally

    $ a = "hello "
    $ b = "world"
    $ a + b
    'hello world'

prints out "hello world" (note we had to add an extra space after "hello").

Typing and working with variables one-by-one like this is easy, but would be very time-consuming and prone to error if we had to type in all of this
data line by line. If you want to put large amounts of data into a program, then one of the best ways of doing this is to read it from a file.

## File reading

Python is great at processing text and reading and writing files. Lets type in the following;

    $ ipython
    FILE = open(“README.md”, “r”)
    lines = FILE.readlines()
    i = 0
    for line in lines:
        i = i + 1
        print “%4d: %s” % (i, line),

What you should see is that Python has printed out every line of the file, with each line preceeded by its line number. 

    1: # Software Carpentry at Exeter 2013
    2: 
    3: ![Software Carpentry logo](http://software-carpentry.org/img/software-carpentry-banner.png "Software Carpentry logo")
    4: 
    5: Thursday 14-Friday 15 November 2013.

Lets go through each line to see how Python has achieved this feat.

The first step was to open the file. You open files using the “open” command, e.g.

    FILE = open(“README.md”, “r”)

opens the file called “README.md”. The “r” tells Python to open the file for “reading”. We will use “w” later on to open 
files for “writing”.

The file is opened and a file handle object is returned, which we have assigned to the variable “FILE”. This
handle provides the means to interact with the file. We could have called it anything we want, e.g. 

    TURTLE = open(“README.md”, “r”)
    PUSSYCAT = open(“README.md”, “r”)

would open the file and return handles called “TURTLE” and “PUSSYCAT”. Note that, by convention, we tend
to use capital letters to name file handles, and, normally, you should use reasonable names (TURTLE is perhaps
not reasonable, unless it is a file containing turtle-related data?). Note also that you can open and file as
many times as you want, and attach it to as many file handles as you want, with each one acting independently.

So, what is a file handle? We can use the help provided by Python to take a look. Python provides “help” which 
can be used on any variable. Type;

    help(FILE)

    Help on file object:
    
    class file(object)
     |  file(name[, mode[, buffering]]) -> file object
     |  
     |  Open a file.  The mode can be 'r', 'w' or 'a' for reading (default),
     |  writing or appending.  The file will be created if it doesn't exist
     |  when opened for writing or appending; it will be truncated when 
     |  opened for writing.  Add a 'b' to the mode for binary files.
     |  Add a '+' to the mode to allow simultaneous reading and writing.
     |  If the buffering argument is given, 0 means unbuffered, 1 means line
     |  buffered, and larger numbers specify the buffer size.  The preferred way
     |  to open a file is with the builtin open() function.

The filehandle provides a set of functions that can be used to interact with the file. Interesting functions
are “readline” and “readlines”. Scroll down to take a look at the documentation…

     |  readline(...)
     |      readline([size]) -> next line from the file, as a string.
     |      
     |      Retain newline.  A non-negative size argument limits the maximum
     |      number of bytes to return (an incomplete line may be returned then).
     |      Return an empty string at EOF.
     |  
     |  readlines(...)
     |      readlines([size]) -> list of strings, each a line from the file.
     |      
     |      Call readline() repeatedly and return a list of the lines so read.
     |      The optional size argument, if given, is an approximate bound on the
     |      total number of bytes in the lines returned.

As you can see, “readline” reads and returns a single line from the file, e.g.

     line = FILE.readline()
     print line

     # Software Carpentry at Exeter 2013

We can read each line, one by one, using “readline”, e.g.

     line = FILE.readline()
     print line
     
     
     line = FILE.readline()
     ![Software Carpentry logo](http://software-carpentry.org/img/software-carpentry-banner.png "Software Carpentry logo")

We can also read lines using a loop, e.g. read the next 5 lines

     for i in range(0,5):
         line = FILE.readline()
         print line

    Thursday 14-Friday 15 November 2013.
    
    
    
    ## Timetable
    
    
    
    Thursday 14th
    


## Lists

Lists, which are also called arrays or vectors, provide a simple list of variables. In python, we create lists using square brackets

    $ a = [ "cat", "dog", "horse", "fish" ]

This has created a list containing four strings, "cat", "dog", "horse" and "fish". To access each item we also use square brackets

    $ a[0]
    'cat'

prints "cat", as it accesses the first item in the list.

    $ a[1]
    'dog'

prints "dog", as it accesses the second item in the list. As you can probably guess, a[3] will print "fish" as it accesses the fourth item

    $ a[3]
    'fish'

In python, you can also work from the back of the list, e.g.

    $ a[-1]
    'fish'

prints the last item,

    $ a[-2]
    'horse'

prints the second to last item etc. If you access an item that doesn't exist, then you get an error.

    $ a[4]

gives an "index out of range" error.

To get the number of items in the list, we have to use "len"

    $ len(a)
    4

This prints "4", as we have four things in the list.

We can also change the value of an item by setting it equal to a new value

    $ a[0] = 20
    $ a
    [20, 2, 3, 4]

### Functions of a List

A list comes with lots of useful abilities. You can see the list of abilities in ipython by pressing tab

    $ a.[TAB]
    a.append   a.count    a.extend   a.index    a.insert   a.pop      a.remove   a.reverse  a.sort

The abilities are provided by functions, for example "append". We can see what the function does by using python's help

    $ help(a.append)
    
    Help on built-in function append:

    append(...)
        L.append(object) -- append object to end

So append is used to add items onto the end of the list. For example

    $ a.append("gerbil")
    $ a
    ['cat', 'dog', 'horse', 'fish', 'gerbil']

has added the string "gerbil" onto the end of the list. There are other functions, e.g.

    $ a.remove("dog")
    $ a
    ['cat', 'horse', 'fish', 'gerbil']

has removed the string "dog".

### Looping over a list

You can iterate over all items in a list using a loop, for example

    $ for i in range(0, len(a)):
    $     print( a[i] )
    
    cat
    horse
    fish
    gerbil

This can be useful, for example, for adding together two sets of numbers;

    $ x = [ 1, 2, 3, 4 ]
    $ y = [ 5, 6, 7, 8 ]
    $ z = []
    $ for i in range(0, len(x)):
    $     z.append( x[i] + y[i] )
    $
    $ z
    
    [6, 8, 10, 12]

### Nesting lists

Lists can contain a mixture of any type of data. For example, you can mix numbers and strings

    $ a = [ "cat", 15, 6.5 ]
    $ a
    ['cat', 15, 6.5]

Lists can also contain other lists, for example,

    $ matrix = [ [1,2,3,4], [5,6,7,8], [9,10,11,12] ]
    $ matrix
    [[1, 2, 3, 4], [5, 6, 7, 8], [9, 10, 11, 12]]

This is called "nesting" one list inside another. Accessing the sub-list, or items within it is easy.

    $ matrix[1]
    [5, 6, 7, 8]
    $ matrix[1][2]
    7

You can nest lists as deeply as you want, creating a multidimensional matrix.

    $ matrix = [ [ [ [ [ 5 ] ] ] ] ]
    $ matrix[0][0][0][0][0]
    5

## Dictionaries

Lists let you store lots of variables, and to access them by their location in the list. However, there are lots of times when you want to store lots of variables, but access them using more complex relationships. One example is a dictionary, which lets you store variables and access them using a key. 

Dictionaries in python are represented using curly brakets

    $ a = { "cat" : "mieow", "dog" : "woof", "horse" : "neigh" }

Here I am storing four key-value pairs. I am storing the value "mieow", and saying that this is accessed using the key "cat". 

    $ a["cat"]
    'mieow'

Similarly, I have stored the value "woof", and have said that this is accessed using the key "dog"

    $ a["dog"]
    'woof'

Like lists, dictionaries also come with a lot of useful functions, which we can show using the TAB key in ipython

    $ a.[TAB]
    a.clear       a.get         a.iteritems   a.keys        a.setdefault  a.viewitems   
    a.copy        a.has_key     a.iterkeys    a.pop         a.update      a.viewkeys    
    a.fromkeys    a.items       a.itervalues  a.popitem     a.values      a.viewvalues  

and that we can get help with using help()

    $ help(a.keys)
    Help on built-in function keys:

    keys(...)
        D.keys() -> list of D's keys

The keys() function thus returns a list of all of the keys

    $ a.keys()
    ['horse', 'dog', 'cat']

while the values() function returns the list of all of the values

    $ a.values()
    ['neigh', 'woof', 'mieow']

We can change items in the dictionary by setting them equal to a new value

    $ a["dog"] = "bark"
    $ a
    {'cat': 'mieow', 'dog': 'bark', 'horse': 'neigh'}

We can also use this to add new items to the dictionary

    $ a["fish"] = "bubble"
    $ a
    {'cat': 'mieow', 'dog': 'bark', 'fish': 'bubble', 'horse': 'neigh'}

### Looping over a dictionary

As the keys() function returns the list of all keys in a dictionary, the best way to loop over all items in a dictionary is to loop over the list of keys

    $ keys = a.keys()
    $ for i in range(0,len(keys)):
    $     print("%s == %s" % (keys[i], a[keys[i]]))
    
    horse == neigh
    dog == bark
    fish == bubble
    cat == mieow

You could print them out in alphabetical order by using the sort() function of a list to sort the keys before looping

    $ keys.[TAB]
    keys.append   keys.extend   keys.insert   keys.remove   keys.sort     
    keys.count    keys.index    keys.pop      keys.reverse  

    $ keys.sort()
    $ keys
    ['cat', 'dog', 'fish', 'horse']

    $ for i in range(0,len(keys)):
    $     print("%s == %s" % (keys[i], a[keys[i]]))

    cat == mieow
    dog == bark
    fish == bubble
    horse == neigh

### Nesting dictionaries

Like lists, dictionaries can contain any type of data, and you can also nest dictionaries and lists inside each other.

    $ a = { "cat" : 5, "dog" : ["walk", "feed", "sleep"], "fish" : {"type" : "goldfish"} }
    $ a["cat"]
    5
    $ a["dog"]
    ['walk', 'feed', 'sleep']
    $ a["dog"][1]
    'feed'
    $ a["fish"]["type"]
    'goldfish'

You can also create the above dictionary item-by-item

    $ a = {}
    $ a["cat"] = 5
    $ a["dog"] = [ "walk", "feed", "sleep" ]
    $ a["fish"] = { "type" : "goldfish" }
    $ a
    {'cat': 5, 'dog': ['walk', 'feed', 'sleep'], 'fish': {'type': 'goldfish'}}


## Strings as lists

Finally, we will finish this session by noting that strings are actually lists. A string is a list container of letters.

    $ a = "hello world"
    $ len(a)
    11
    $ a[0]
    'h'
    $ a[-1]
    'd'

We can loop over all letters in a string using

    $ for i in range(0,len(a)):
    $     print(a[i])
    h 
    e
    l
    l
    o
     
    w
    o
    r
    l
    d

Python provides a nice shorthand for looping over every item in a list

    $ for letter in a:
    $    print letter

will print the same output.

You can also create a string from a list of letters. For this, you need to import and use the "string" module from python

    $ import string
    $ a = ['h', 'e', 'l', 'l', 'o']
    $ a
    ['h', 'e', 'l', 'l', 'o']

    $ s = string.join(a)
    $ s
    'h e l l o'

Note that string.join has added a space between each letter. Using help() we can see how to remove this space

    $ help(string.join)
    Help on function join in module string:
    
    join(words, sep=' ')
        join(list [,sep]) -> string
    
        Return a string composed of the words in list, with
        intervening occurrences of sep.  The default separator is a
        single space.
    
        (joinfields and join are synonymous)

    $ s = string.join(a, "")
    $ s
    'hello'

## Exercise

You should have the files for the exercises as they were downloaded when you cloned the repository. They are located in the "Python" directory.

### Exercise 1a

Here is a script, [1a/encode.py](1a/encode.py) which contains a dictionary for converting the alphabet to Morse code, and a string that must be converted (quite quickly!).

    letter_to_morse = {'a':'.-', 'b':'-...', 'c':'-.-.', 'd':'-..', 'e':'.', 'f':'..-.',
                       'g':'--.', 'h':'....', 'i':'..', 'j':'.---', 'k':'-.-', 'l':'.-..', 'm':'--',
                       'n':'-.', 'o':'---', 'p':'.--.', 'q':'--.-', 'r':'.-.', 's':'...', 't':'-',
                       'u':'..-', 'v':'...-', 'w':'.--', 'x':'-..-', 'y':'-.--', 'z':'--..',
                       '0':'-----', '1':'.----', '2':'..---', '3':'...--', '4':'....-',
                       '5':'.....', '6':'-....', '7':'--...', '8':'---..', '9':'----.',
                       ' ':'/' }

    message = "SOS We have hit an iceberg and need help quickly"

You should find a copy of this script in your directory (in [1a/encode.py](1a/encode.py)).

Use what you have learned about lists and dictionaries to loop through each letter in the message, look-up the corresponding Morse code for that letter, and join the result together to create a string that contains the Morse code that will be transmitted to save the ship. Note that the dictionary contains only lowercase letters, so you will need to use "TAB" and help() to find a function to convert uppercase letters to lowercase.

If you are really stuck, then there is an example completed script available to read in [1a/example/encode.py](1a/example/encode.py).

### Exercise 1b

You have just received the Morse code message in the script [1b/decode.py](1b/decode.py). You need to decode this message back to English.

    letter_to_morse = {'a':'.-', 'b':'-...', 'c':'-.-.', 'd':'-..', 'e':'.', 'f':'..-.', 
                       'g':'--.', 'h':'....', 'i':'..', 'j':'.---', 'k':'-.-', 'l':'.-..', 'm':'--', 
                       'n':'-.', 'o':'---', 'p':'.--.', 'q':'--.-', 'r':'.-.', 's':'...', 't':'-',
                       'u':'..-', 'v':'...-', 'w':'.--', 'x':'-..-', 'y':'-.--', 'z':'--..',
                       '0':'-----', '1':'.----', '2':'..---', '3':'...--', '4':'....-',
                       '5':'.....', '6':'-....', '7':'--...', '8':'---..', '9':'----.',
                       ' ':'/' }

    message = "... --- ... / .-- . / .... .- ...- . / .... .. - / .- -. / .. -.-. . -... . .-. --. / .- -. -.. / -. . . -.. / .... . .-.. .--. / --.- ..- .. -.-. -.- .-.. -.--"

You should find a copy of this script in your directory (in [1b/decode.py](1b/decode.py)).

Use what you have learned about lists and dictionaries to loop through Morse letters in the Morse code message, and convert them back to English. Note that "letter_to_morse" is a dictionary that goes from letters to Morse code. You will need to first invert this dictionary to let you look up the letter from the Morse code (if you need help, look at [1b/example/invert.py](1b/example/invert.py)). Morse code letters are separated by spaces. Use ipython TAB and help() to find a function that will split the message into letters.

If you are really stuck, then there is an example completed script available to read in [1b/example/decode.py](1b/example/decode.py).

### Extension

If you have time, combine your completed "encode.py" and "decode.py" scripts into a single script that converts a message from English to Morse code, and then converts it back again into English.

## Version Control

When you have finished, commit all of your changes to your Git repository.

    $ git commit -am "...commit message..."
    $ git push

# [Up](python_and_good_programming_practice.md) [Next](2_functions_and_modules.md)