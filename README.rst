virtualenvwrapper-wintcc
========================

This is a port of David Marble's `virtualenvwrapper-win <https://github.com/davidmarble/virtualenvwrapper-win/>`_
to JPSoft's Take Command/TCC batch scripts.

David Marble's virtualenvwrapper-win is a port of Doug Hellmann's 
`virtualenvwrapper <http://www.doughellmann.com/projects/virtualenvwrapper/>`_ 
to Windows batch scripts.  The idea behind virtualenvwrapper is to ease usage of 
Ian Bicking's `virtualenv <http://pypi.python.org/pypi/virtualenv>`_, a tool 
for creating isolated Python virtual environments, each with their own libraries 
and site-packages.

These scripts should work on any version of Windows (Windows XP, Windows Vista, Windows 7).  I modified and tested these scripts against Take Command 12.11.  Although not tested, these scripts should be compatible with any newer version of Take Command as well as being compatible with the free-for-personal-use TCC/LE.  Check out `JP Software <http://jpsoft.com/>`_ for more info about their command prompt.

However, they only work in the **Take Command command prompt or TCC**. They **will not work in Powershell or the regular command prompt.**  There are other virtualenvwrapper projects out there for Powershell. 


Installation
------------
**For Windows only with Take Command or TCC installed**

Installed scripts are placed in the main directory of the active python installation. For example, if your default python is under C:\Python27\, these scripts will be in that same directory.

To install, run one of the following::

    # using pip
    pip install virtualenvwrapper-wintcc

    # using easy_install
    easy_install virtualenvwrapper-wintcc
    
    # from source
    git clone git://github.com/silicon_ghost/virtualenvwrapper-wintcc.git
    cd virtualenvwrapper-wintcc
    python setup.py install

**Optional**: Add an environment variable WORKON_HOME to specify the path to store environments. By default, this is ``%USERPROFILE%\Envs``.

**Optional**: **pywin** python version switcher (not included)

If you use several versions of python, you can switch between them using a separate project `pywin <https://github.com/davidmarble/pywin>`_. It's a lightweight python 2.5-3.3 launcher and switcher David Marble wrote for the Windows command line and MSYS/MINGW32. It's similar to the `py.exe launcher/switcher available in python 3.3 <http://docs.python.org/3/using/windows.html#launcher>`_, but written with basic Windows batch scripts and a shell script for MSYS/MINGW32 support. 

Main Commands
-------------
``mkvirtualenv <name>``
    Create a new virtualenv environment named *<name>*.  The environment will 
    be created in WORKON_HOME.

``lsvirtualenv``
    List all of the enviornments stored in WORKON_HOME.

``rmvirtualenv <name>``
    Remove the environment *<name>*. 

``workon [<name>]``
    If *<name>* is specified, activate the environment named *<name>* (change 
    the working virtualenv to *<name>*). If a project directory has been 
    defined, we will change into it. If no argument is specified, list the 
    available environments. 

``deactivate``
    Deactivate the working virtualenv and switch back to the default system 
    Python.

``add2virtualenv <full or relative path>``
    If a virtualenv environment is active, appends *<path>* to 
    ``virtualenv_path_extensions.pth`` inside the environment's site-packages,
    which effectively adds *<path>* to the environment's PYTHONPATH. 
    If a virtualenv environment is not active, appends *<path>* to
    ``virtualenv_path_extensions.pth`` inside the default Python's 
    site-packages. If *<path>* doesn't exist, it will be created.
    
Convenience Commands
--------------------
``cdproject``
    If a virtualenv environment is active and a projectdir has been defined,
    change the current working directory to active virtualenv's project directory.
    ``cd-`` will return you to the last directory you were in before calling 
    ``cdproject`` (Note that this is not exactly the same behavior as ``cd -`` 
    in TCC).

``cdsitepackages``
    If a virtualenv environment is active, change the current working 
    directory to the active virtualenv's site-packages directory. If 
    a virtualenv environment is not active, change the current working 
    directory to the default Python's site-packages directory. ``cd-`` 
    will return you to the last directory you were in before calling 
    ``cdsitepackages`` (Note that this is not exactly the same behavior as 
    ``cd -`` in TCC).

``cdvirtualenv``
    If a virtualenv environment is active, change the current working 
    directory to the active virtualenv base directory. If a virtualenv 
    environment is not active, change the current working directory to 
    the base directory of the default Python. ``cd-`` will return you 
    to the last directory you were in before calling ``cdvirtualenv``
    (Note that this is not exactly the same behavior as ``cd -`` in TCC).

``lssitepackages``
    If a virtualenv environment is active, list that environment's 
    site-packages. If a virtualenv environment is not active, list the 
    default Python's site-packages. Output includes a basic listing of 
    the site-packages directory, the contents of easy-install.pth, 
    and the contents of virtualenv_path_extensions.pth (used by 
    ``add2virtualenv``).

``setprojectdir <full or relative path>``
    If a virtualenv environment is active, define *<path>* as project 
    directory containing the source code.  This allows the use of ``cdproject``
    to change the working directory. In addition, the directory will be 
    added to the environment using ``add2virtualenv``. If *<path>* doesn't 
    exist, it will be created.

``toggleglobalsitepackages``
    If a virtualenv environment is active, toggle between having the 
    global site-packages in the PYTHONPATH or just the virtualenv's
    site-packages.

``whereis <file>``
    A script included for convenience. Returns directory locations 
    of `file` and `file` with any executable extensions. So you can call 
    ``whereis python`` to find all executables starting with ``python`` or 
    ``whereis python.exe`` for an exact match.  This is similar to the
    ``which <file>`` command in TCC.
    
Software Credits
----------------
virtualenvwrapper-win by David Marble
Licensed Under: BSD 3-Clause License (Revised)

Acknowledgements
----------------
David Marble, Doug Hellmann, and Ian Bicking did all of the heavy lifting that makes this work.  My contribution is simply to allow these scripts to run well in the Take Command/TCC shell.

