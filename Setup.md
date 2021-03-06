# Software Installation
Please make sure you try to install everything before coming to the 
bootcamp so that teaching can begin right away.
(Wireless networks usually can't cope with lots of people trying to download these packages at the same time...)
If you run into any problems,
please let your boot camp organizer know as soon as possible.

**You do *not* need to install everything listed below, since some packages are alternatives to one another.**

## Already set-up? Do some testing. 
You may already have all the tools you need for the bootcamp installed! 
You should check that you have the following software and tools available.
If this is the case, or have followed the instructions below, then you can check your installation using our [setup test scripts](setup/README.md). 

* Web browser
* Bash shell - other shells are OK (e.g [Cygwin](http://cygwin.org)) but please ensure they support the commands `grep`, `find`, `awk`, `cat`, `history`.
* A text editor e.g. nano, vi or emacs
* [Git](http://git-scm.com/)
* Python 2.6 or 2.7
* Python [ipython](http://ipython.org)
* Python [nose](https://nose.readthedocs.org/en/latest/)
* R [website](http://www.stats.bris.ac.uk/R/) and [R studio](http://rstudio.com) 

Otherwise, follow the instructions below for your operating system

##Using a Virtual Machine

Installation issues can and do happen. To ensure that you
can continue to participate in a lesson even if one of your
software programs fails, we provide a Linux virtual machine
that contains all the necessary software
pre-installed. Please install
[VirtualBox](https://www.virtualbox.org/)
and download
[this virtual machine image](http://tinyurl.com/exeter-swc-vm). 

Load the VM into VirtualBox by doing `Import Appliance` and loading the `.ova` file.

##Native Installation
Many people prefer to install software directly on their machine
so that it is integrated with their usual desktop environment.
Even if you plan to do this,
please download VirtualBox and the virtual machine as a backup - it
can be difficult to get everything set up correctly on older machines.

###Windows
The [Software Carpentry Installer](setup/swc-windows-installer.py)
installs several of the packages described below.
After first installing Python and a shell save the file to your hard drive,
then double-click on the file to run it.

####The Unix Bash Shell
Follow [these instructions](https://openhatch.org/missions/windows-setup/install-git-bash)
to install [Git Bash](http://msysgit.github.com/).

####Git
See "The Unix Bash Shell" above.

####Python
We recommend the all-in-one scientific Python distributions
[Anaconda](http://continuum.io/downloads.html) and
[Canopy](https://www.enthought.com/products/canopy/).
Anaconda and Canopy Express are free to everyone, Canopy is free to academics.
Setting these packages up may require using the shell;
if you aren't comfortable doing this,
please download the installer corresponding to your operating system
*before* arriving and your instructor will help you set it up.

####R and R studio
Go to the [R project download page](http://www.r-project.org), click on the Download link 
(CRAN) in the sidebar and select a mirror near to you. [Bristol](http://www.stats.bris.ac.uk/R/) may be the best option. 
Download the Windows binary and run it to install R.
With R installed, go to the [Rstudio](http://www.rstudio.com/ide/download/desktop) download page and select the appropriate version for your operating system. 
Install this - you may need to have administrator rights.

###Mac OS X
Bash is the default shell in Mac OS X and this should be installed.

####Git
Use the [Git installer](http://code.google.com/p/git-osx-installer/downloads/list?can=3)
(the faster and simpler option) or install XCode and the command line tools (from the Download preferences pane).
Note that the XCode download is over a gigabyte (see below)...

####Python
We recommend the all-in-one scientific Python distributions
[Anaconda](http://continuum.io/downloads.html) and
[Canopy](https://www.enthought.com/products/canopy/).
Anaconda and Canopy Express are free to everyone, Canopy is free to academics.
Setting these packages up may require using the shell;
if you aren't comfortable doing this,
please download the installer corresponding to your operating system
*before* arriving and your instructor will help you set it up.

####Supporting Tools
[XCode](https://developer.apple.com/xcode/)
is a set of free developer tools for Mac OS X.
To install it:
* Go to the Apple app store.
* Search for XCode.
* Click *Free*.
* Click *Install App*.

Note that the XCode download is over a gigabyte,
so please do this **before** arriving at the boot camp.

####R and R studio
Go to the [R project download page](http://www.r-project.org), click on the Download link 
(CRAN) in the sidebar and select a mirror near to you. [Bristol](http://www.stats.bris.ac.uk/R/) may be the best option. 
Download the Mac binary installer and run it to install R.
With R installed, go to the [Rstudio](http://www.rstudio.com/ide/download/desktop) download page and select the appropriate version for your operating system. 
Install this and an Rstudio app should appear in your Applications folder.

###Linux
Below there are brief instructions. More details for RedHat/Scientific Linux 6 and Ubuntu 12.10 are found at the bottom of the page. 

####The Unix Bash Shell
Bash is usually the default shell,
but if your Linux installation gives you something else
you can run Bash by opening a terminal and typing `bash`.

####Git
Git should already be installed on your machine.
To check, type `which git` at the command line.
If it is not found, install it via your distribution's package manager
(e.g., `apt-get`).

####Python
We recommend the all-in-one scientific Python distributions
[Anaconda](http://continuum.io/downloads.html) and
[Canopy](https://www.enthought.com/products/canopy/).
Anaconda and Canopy Express are free to everyone, Canopy is free to academics.
Setting these packages up may require using the shell;
if you aren't comfortable doing this,
please download the installer corresponding to your operating system
*before* arriving and your instructor will help you set it up.


#### To install under RedHat/Scientific Linux 6

Scientific Linux 6 already comes with shell and vi text editor. To install the other packages run,

    $ sudo su -
    # yum install nano
    # yum install git
    # yum install python
    # yum install python-nose
    # nosetests
    ------------------------------------------------------------------
    Ran 0 tests in 0.003s
    OK
    # yum install python-coverage
    # nosetests --with-coverage
    ...
    # yum install pytest
    # py.test
    ===================== test session starts ======================
    platform linux2 -- Python 2.6.6 -- pytest-2.3.4
    collected 0 items 
    =======================  in 0.01 seconds =======================
    # yum install python-pip
    # pip-python install pytest-cov
    # py.test --cov .
    ===================== test session starts ======================
    platform linux2 -- Python 2.6.6 -- pytest-2.3.4
    plugins: cov
    collected 0 items 
    Coverage.py warning: No data was collected.
    ------- coverage: platform linux2, python 2.6.6-final-0 --------
    Name    Stmts   Miss  Cover
    ---------------------------
    =======================  in 0.05 seconds =======================
    $ easy_install ipython
    $ ipython
    Python 2.6.6 (r266:84292, Jun 18 2012, 09:57:52) 
    Type "copyright", "credits" or "license" for more information.

    IPython 0.10 -- An enhanced Interactive Python.
    ?         -> Introduction and overview of IPython's features.
    %quickref -> Quick reference.
    help      -> Python's own help system.
    object?   -> Details about 'object'. ?object also works, ?? prints more.

    In [1]: CTRL-D
    $ yum install numpy
    $ python
    >>> import numpy
    >>> print numpy.__version__
    >>> from numpy import *
    >>> from numpy.linalg import *
    >>> a = array([[1.0, 2.0], [3.0, 4.0]])
    >>> eig(a)
    >>> CTRL-D
    $ yum install scipy
    $ python
    >>> import scipy
    >>> print scipy.__version__
    >>> from scipy import *
    >>> a = zeros(1000)
    >>> a[:100]=1
    >>> b=fft(a)
    >>> print b
    >>> CTRL-D
    $ yum install python-matplotlib
    $ python
    >>> import matplotlib
    >>> print matplotlib.__version__
    >>> CTRL-D
    $ ipython -pylab
    In []: plot([1,2,3])
    In []: from scipy import *
    In []: a = zeros(1000)
    In []: a[:100]=1
    In []: b=fft(a)
    In []: plot(abs(b))

#### To install under Ubuntu

Ubuntu 12.10 and above already comes with shell, vi and nano text editors, Python 2.7. To install the other packages run,

    $ sudo su -
    # apt-get install nano
    # apt-get install git
    # apt-get install python
    # apt-get install python-nose
    # nosetests
    ------------------------------------------------------------------
    Ran 0 tests in 0.003s
    OK
    # apt-get install python-coverage
    # nosetests --with-coverage
    ...

    # apt-get install python-pytest
    # py.test
    ===================== test session starts ===================== 
    platform linux2 -- Python 2.7.3 -- pytest-2.3.4
    collected 0 items 
    ===================== in 0.00 seconds ===================== 
    # apt-get install python-pip
    # pip install pytest-cov
    # py.test --cov .
    ===================== test session starts ======================
    platform linux2 -- Python 2.7.3 -- pytest-2.2.4
    collected 0 items 
    Coverage.py warning: No data was collected.
    ------- coverage: platform linux2, python 2.7.3-final-0 --------
    Name    Stmts   Miss  Cover
    ---------------------------
    =======================  in 0.03 seconds =======================
    $ easy_install ipython
    $ ipython
    Python 2.7.3 (default, Sep 26 2012, 21:53:58) 
    Type "copyright", "credits" or "license" for more information.

    IPython 0.13.1 -- An enhanced Interactive Python.
    ?         -> Introduction and overview of IPython's features.
    %quickref -> Quick reference.
    help      -> Python's own help system.
    object?   -> Details about 'object', use 'object??' for extra details.

    In [1]: CTRL-D
    $ apt-get install python-numpy
    $ python
    >>> import numpy
    >>> print numpy.__version__
    >>> from numpy import *
    >>> from numpy.linalg import *
    >>> a = array([[1.0, 2.0], [3.0, 4.0]])
    >>> eig(a)
    >>> CTRL-D
    $ apt-get install python-scipy
    $ python
    >>> import scipy
    >>> print scipy.__version__
    >>> from scipy import *
    >>> a = zeros(1000)
    >>> a[:100]=1
    >>> b=fft(a)
    >>> print b
    >>> CTRL-D
    $ apt-get install python-matplotlib
    $ python
    >>> import matplotlib
    >>> print matplotlib.__version__
    >>> CTRL-D
    $ ipython -pylab
    In []: plot([1,2,3])
    In []: from scipy import *
    In []: a = zeros(1000)
    In []: a[:100]=1
    In []: b=fft(a)
    In []: plot(abs(b))

###R and R studio
####R - Preferred method
Use your distributions package manager to install the r-base (or r-base-core) package

####R - alternative methods
Go to the [R project download page](http://www.r-project.org), click on the Download link 
(CRAN) in the sidebar and select a mirror near to you. [Bristol](http://www.stats.bris.ac.uk/R/) may be the best option. 
Download the linux binary installer and run it to install R.

Or, more painfully, download and install from source. There are so many variations that at this point detailed instructions probably won't help.
Read and follow the install documentation for your distribution

####R Studio
With R installed, go to the [Rstudio](http://www.rstudio.com/ide/download/desktop) download page and select the appropriate version for your operating system. 
Use your package manager to install this package and any dependencies. You will probably require superuser (sudo) access. 
On Ubuntu you may also have to install dependent packages such as libjpeg62

    > sudo dpkg -i rstudio.deb
    > sudo apt-get install libjpeg62
