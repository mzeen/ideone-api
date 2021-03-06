===================
 Ideone Python API
===================

`Ideone`_ is a pastebin, as well as an online compiler and debugger.
This project is a Pythonic binding to the `Ideone API`_.

Installation
============

The Ideone API can also be installed with ``pip`` from `PyPI`_ using
``pip install ideone``.  Alternately, you can clone the repository and
use setup.py like so ::

    git clone https://github.com/jschaf/ideone-api.git
    cd ideone-api
    python setup.py install

Getting Started
===============

You need an Ideone account and an *API password* which you can create
at the `Ideone registration page`_.  After that, open up a Python
shell and begin hacking. ::

    >>> from ideone import Ideone
    >>> i = Ideone('username', 'APIpassword')
    >>> i.test()
    {'answerToLifeAndEverything': 42,
     'error': "OK",
     'moreHelp': "ideone.com",
     'oOok': True,
     'pi': 3.14}

    >>> i.create_submission('print(42)', language_name='python')
    {'error': 'OK',
     'link' : 'LsSbo'}

    >>> i.create_submission('print(42)', language_id=166)
    {'error': 'OK',
     'link' : 'FDfrM'}

    >>> i.submission_details('LsSbo')
    {'cmpinfo': "",
     'date': "2011-04-18 15:24:14",
     'error': "OK",
     'input': "",
     'langId': 116,
     'langName': "Python 3",
     'langVersion': "python-3.1.2",
     'memory': 5852,
     'output': 42,
     'public': True,
     'result': 15,
     'signal': 0,
     'source': "print(42)",
     'status': 0,
     'stderr': "",
     'time': 0.02}

    >>> i.languages()
    {'error': 'OK',
    'languages': {1: "C++ (gcc-4.3.4)",
                  2: "Pascal (gpc) (gpc 20070904)",
                  ...
                  ...
                  ...
                  125: "Falcon (falcon-0.9.6.6)"}}


Supported Languages
===================

As of 27 May 2012, Ideone supports the following languages.  You don't
need to use the full names for ``language_name``.  The simplified name
works just as well with this API.

+-------+----------------------------------------------+-----------------+
| Index | Ideone Full Name                             | Simplified Name |
+=======+==============================================+=================+
|     1 | C++ (gcc-4.3.4)                              | C++             |
+-------+----------------------------------------------+-----------------+
|     2 | Pascal (gpc) (gpc 20070904)                  | Pascal          |
+-------+----------------------------------------------+-----------------+
|     3 | Perl (perl 5.12.1)                           | Perl            |
+-------+----------------------------------------------+-----------------+
|     4 | Python (python 2.7.2)                        | Python          |
+-------+----------------------------------------------+-----------------+
|     5 | Fortran (gfortran-4.3.4)                     | Fortran         |
+-------+----------------------------------------------+-----------------+
|     6 | Whitespace (wspace 0.3)                      | Whitespace      |
+-------+----------------------------------------------+-----------------+
|     7 | Ada (gnat-4.3.2)                             | Ada             |
+-------+----------------------------------------------+-----------------+
|     8 | Ocaml (ocamlopt 3.10.2)                      | Ocaml           |
+-------+----------------------------------------------+-----------------+
|     9 | Intercal (c-intercal 28.0-r1)                | Intercal        |
+-------+----------------------------------------------+-----------------+
|    10 | Java (sun-jdk-1.6.0.31)                      | Java            |
+-------+----------------------------------------------+-----------------+
|    11 | C (gcc-4.3.4)                                | C               |
+-------+----------------------------------------------+-----------------+
|    12 | Brainf**k (bff-1.0.3.1)                      | Brainf**k       |
+-------+----------------------------------------------+-----------------+
|    13 | Assembler (nasm-2.07)                        | Assembler       |
+-------+----------------------------------------------+-----------------+
|    14 | CLIPS (clips 6.24)                           | CLIPS           |
+-------+----------------------------------------------+-----------------+
|    15 | Prolog (swi) (swipl 5.6.64)                  | Prolog          |
+-------+----------------------------------------------+-----------------+
|    16 | Icon (iconc 9.4.3)                           | Icon            |
+-------+----------------------------------------------+-----------------+
|    17 | Ruby (ruby-1.9.2)                            | Ruby            |
+-------+----------------------------------------------+-----------------+
|    19 | Pike (pike 7.6.86)                           | Pike            |
+-------+----------------------------------------------+-----------------+
|    21 | Haskell (ghc-6.8.2)                          | Haskell         |
+-------+----------------------------------------------+-----------------+
|    22 | Pascal (fpc) (fpc 2.2.0)                     | Pascal          |
+-------+----------------------------------------------+-----------------+
|    23 | Smalltalk (gst 3.1)                          | Smalltalk       |
+-------+----------------------------------------------+-----------------+
|    25 | Nice (nicec 0.9.6)                           | Nice            |
+-------+----------------------------------------------+-----------------+
|    26 | Lua (luac 5.1.4)                             | Lua             |
+-------+----------------------------------------------+-----------------+
|    27 | C# (mono-2.8)                                | C#              |
+-------+----------------------------------------------+-----------------+
|    28 | Bash (bash 4.0.35)                           | Bash            |
+-------+----------------------------------------------+-----------------+
|    29 | PHP (php 5.2.11)                             | PHP             |
+-------+----------------------------------------------+-----------------+
|    30 | Nemerle (ncc 0.9.3)                          | Nemerle         |
+-------+----------------------------------------------+-----------------+
|    32 | Common Lisp (clisp) (clisp 2.47)             | Common Lisp     |
+-------+----------------------------------------------+-----------------+
|    33 | Scheme (guile) (guile 1.8.5)                 | Scheme          |
+-------+----------------------------------------------+-----------------+
|    34 | C99 strict (gcc-4.3.4)                       | C99 strict      |
+-------+----------------------------------------------+-----------------+
|    35 | JavaScript (rhino) (rhino-1.6.5)             | JavaScript      |
+-------+----------------------------------------------+-----------------+
|    36 | Erlang (erl-5.7.3)                           | Erlang          |
+-------+----------------------------------------------+-----------------+
|    38 | Tcl (tclsh 8.5.7)                            | Tcl             |
+-------+----------------------------------------------+-----------------+
|    39 | Scala (scala-2.9.1)                          | Scala           |
+-------+----------------------------------------------+-----------------+
|    40 | SQL (sqlite3-3.7.3)                          | SQL             |
+-------+----------------------------------------------+-----------------+
|    43 | Objective-C (gcc-4.5.1)                      | Objective-C     |
+-------+----------------------------------------------+-----------------+
|    44 | C++0x (gcc-4.5.1)                            | C++0x           |
+-------+----------------------------------------------+-----------------+
|    45 | Assembler (gcc-4.3.4)                        | Assembler       |
+-------+----------------------------------------------+-----------------+
|    54 | Perl 6 (rakudo-2010.08)                      | Perl 6          |
+-------+----------------------------------------------+-----------------+
|    55 | Java7 (sun-jdk-1.7.0_03)                     | Java7           |
+-------+----------------------------------------------+-----------------+
|    62 | Text (text 6.10)                             | Text            |
+-------+----------------------------------------------+-----------------+
|   101 | VB.NET (mono-2.4.2.3)                        | VB.NET          |
+-------+----------------------------------------------+-----------------+
|   102 | D (dmd) (dmd-2.042)                          | D               |
+-------+----------------------------------------------+-----------------+
|   104 | AWK (gawk) (gawk-3.1.6)                      | AWK             |
+-------+----------------------------------------------+-----------------+
|   105 | AWK (mawk) (mawk-1.3.3)                      | AWK             |
+-------+----------------------------------------------+-----------------+
|   106 | COBOL 85 (tinycobol-0.65.9)                  | COBOL 85        |
+-------+----------------------------------------------+-----------------+
|   107 | Forth (gforth-0.7.0)                         | Forth           |
+-------+----------------------------------------------+-----------------+
|   108 | Prolog (gnu) (gprolog-1.3.1)                 | Prolog          |
+-------+----------------------------------------------+-----------------+
|   110 | bc (bc-1.06.95)                              | bc              |
+-------+----------------------------------------------+-----------------+
|   111 | Clojure (clojure 1.3)                        | Clojure         |
+-------+----------------------------------------------+-----------------+
|   112 | JavaScript (spidermonkey) (spidermonkey-1.7) | JavaScript      |
+-------+----------------------------------------------+-----------------+
|   114 | Go (gc-2010-07-14)                           | Go              |
+-------+----------------------------------------------+-----------------+
|   115 | Unlambda (unlambda-2.0.0)                    | Unlambda        |
+-------+----------------------------------------------+-----------------+
|   116 | Python 3 (python-3.1.2)                      | Python 3        |
+-------+----------------------------------------------+-----------------+
|   117 | R (R-2.11.1)                                 | R               |
+-------+----------------------------------------------+-----------------+
|   118 | COBOL (open-cobol-1.0)                       | COBOL           |
+-------+----------------------------------------------+-----------------+
|   119 | Oz (mozart-1.4.0)                            | Oz              |
+-------+----------------------------------------------+-----------------+
|   121 | Groovy (groovy-1.8.6)                        | Groovy          |
+-------+----------------------------------------------+-----------------+
|   122 | Nimrod (nimrod-0.8.8)                        | Nimrod          |
+-------+----------------------------------------------+-----------------+
|   123 | Factor (factor-0.93)                         | Factor          |
+-------+----------------------------------------------+-----------------+
|   124 | F# (fsharp-2.0.0)                            | F#              |
+-------+----------------------------------------------+-----------------+
|   125 | Falcon (falcon-0.9.6.6)                      | Falcon          |
+-------+----------------------------------------------+-----------------+


.. _ideone: http://ideone.com
.. _Ideone API: http://ideone.com/api
.. _PyPI: http://pypi.python.org/pypi/ideone
.. _Ideone registration page: http://ideone.com/account/register
