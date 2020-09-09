# Regular Expression 

A regular expression is a special sequence of characters that helps you match or find other strings or sets of strings, using a specialized syntax held in a pattern. Regular expressions are widely used in UNIX world.

The Python module **re** provides full support for Perl-like regular expressions in Python. The re module raises the exception re.error if an error occurs while compiling or using a regular expression.


### The match Function

This function attempts to match RE pattern to string with optional flags.

Here is the syntax for this function −

    re.match(pattern, string, flags=0)

The re.match function returns a match object on success, None on failure. We usegroup(num) or groups() function of match object to get matched expression.


### The search Function

This function searches for first occurrence of RE pattern within string with optional flags.

Here is the syntax for this function −

    re.search(pattern, string, flags=0)

The re.search function returns a match object on success, none on failure. We use group(num) or groups() function of match object to get matched expression.

### Search and Replace

One of the most important re methods that use regular expressions is sub.

Syntax

    re.sub(pattern, repl, string, max=0)

This method replaces all occurrences of the RE pattern in string with repl, substituting all occurrences unless max provided. This method returns modified string.



# High-level file operations in Python (shutil)

A number of functions for hgh level operations on files and directories have been defined in shutil module of Python’s standard library.

## copy()

This function copies a file to a specified file in same or other directory. First parameter to the function is a string representation of existing file. Second argument is either name of resultant file or directory. If it is a directory, the file is coped in it with same name. The metadata of original file is not maintained.

    >>> import shutil
    >>> shutil.copy("hello.py","newdir/")
    'newdir/hello.py'

## copy2()

This function is similar to copy() function except for the fact that it retains metadata of source file. For example the date modified property of resulting file will be similar to original file.

    >>> shutil.copy2('person.py', 'newdir/')
    'newdir/person.py'

## move()

This function recursively moves file and directories from on directory to other.

    >>> shutil.move('hello.py', 'newdir/')
    'newdir/hello.py'

## copytree() 

This function recursively copies file and subdirectories in one directory to another directory. Names of two parameters must be string. Directory of second parameter’s name should not exist earlier. To copy individual files copy2() function is internally used.

    >>> shutil.copytree('dir1','dir2')
    'dir2'

## rmtree()

This function removes files and subdirectories in the specified directory.

    >>> shutil.rmtree('dir2')
    >>> shutil.move('hello.py', 'newdir/')
    'newdir/hello.py'

## disk_usage()

This function retrieves usage statistics of directory given.

    >>> shutil.disk_usage('c:\\python36\\dir1')
    usage(total=245681352704, used=84932993024, free=160748359680)

## which()

This function returns path to an executable.

    >>> shutil.which('calc')
    'C:\\WINDOWS\\system32\\calc.EXE'

## make_archive()

This function builds an archive (zip or tar) of files in the root directory.

    >>> root_dir='newdir'
    >>> shutil.make_archive("newdirarch","zip",root_dir)
    'C:\\python36\\newdirarch.zip'

## get_archive_formats()

This function gives of all supported archive formats.

    >>> shutil.get_archive_formats()
    [('bztar', "bzip2'ed tar-file"), ('gztar', "gzip'ed tar-file"), ('tar', 'uncompressed tar file'), ('xztar', "xz'ed tar-file"), ('zip', 'ZIP file')]

## unpack_archive()

This functions extracts files in the given archive. Second parameter is the directory in which file are to be extracted. If not given, the unpacking is performed in current directory.

    >>> shutil.unpack_archive('newdirarch.zip','newdir')









