.. Changelog
   -----------------------------------------------------------------------
   
.. 1.4 - Made top level sections into their own pages including this one
.. 1.3 - Template
	-RST forked. Used to be Ganymede documentation, now used for generating all kinds of system docs
.. 1.2.2 - Add AUG
	-Add Acceptable User Guidelines section
	-Add AUG pdf
	-Add Acceptable User Guidelines hyperlink to pdf
.. 1.2.1 - Compiled with Sphinx
   -Spell correction
   -Added css files to _static in sphinx
   -Added introduction paragraph to 4.2 header

.. 1.2 - Steves Onboarding Updates
   -Spell correction
   -Blurb about CPU core math
   -srun queue info added
   -Added commands to appendix A (appendix v2.0)
   -Updated variables
   
.. 1.1.1 - Mail issues
   - Updated user docs to have the mailto part. 
.. 1.1 - Fixed Issues
   - Updated UTD admin var
   - Added MPI debugging section
   - Added Ganymede Specific section
   - Added show swap mpi
   - Added default vars
.. 1.0 - First Release
   - Minor grammar edits
   - Hid items that aren't live
   - Added Slurm Commands
.. 0.9 - Visual Impovements
   - Fixed pictures to run 
   - Updated Stylesheets to be UTD! Woosh!
   - Created Matlab Section
   - Updated Slurm added inteactive jobs
   - fixed variables
   - added variables for Matlab section
.. 0.8 
   - Fixed Grammatical Error
   - Fixed unicode dashes
   - Added very basic Appendix A
   - Created HTML Documentation using Sphinx
.. 0.7
   - Changed Run Example to Serial and added Parallel 
   - Added scp and rsync
   - Fixed folder locations
   - Fixed quota names
   - Fixed numbers and title capitalization
   - Minor Grammatical edits
   - Added Appendix B - Slurm Commands
.. 0.6
   - built the sections on compilers, modules, and how to run jobs
   - added email and admin variable sections
.. 0.5
   - built out the documentation tree to include 
       - sections space constraints, 
       - compilers and modules, 
       - running jobs, 
       - application specific
   - wrote section 3 on space constraints
   - added variables for the sec 3 tables
.. 0.4
   - Changed from Word Doc to reStructuredText
   - Set Up Automated Feilds
   - Minor Grammatical Edits
.. 0.3
   - Completely created a basic Linux users guide
   - Made minor edits
   - Created heading structure and began reorganization of document
   - Created table of contents
.. 0.2
   - Major Grammar Edits
   - Removed references to 'dead' items
.. 0.1
   - Original version
   
  .. these are the predefined values
   -------------------------------
.. hpc system params
   
.. systemName should just replace mentions of the system's name not including things like domain
.. or user names in code blocks that are upper case of course
.. |systemName| replace:: Ganymede

.. systemNameLower should just replace mentions of the system's name that are lower case, not including
.. things like domain or user names in code blocks
.. |systemNameLower| replace:: ganymede
.. 
.. |hostName| replace:: @ganymede.utdallas.edu

.. |nodecpunum| replace:: 4008
.. |nodememnum| replace:: 14 TB
.. |centVer| replace:: 7.5

.. |matlabver| replace:: r2018a
.. |matlabsitenum| replace:: 12,000
.. |matlabdist| replace:: 32

.. |defcomp| replace:: **Intel**
.. |defmpi| replace:: **mvapich2**

.. admin params
.. |adminemail| replace:: ganymedeadmins@utdallas.edu
.. |mailinglistaddr| replace:: ganymedeusers@lists.utdallas.edu
.. |slurmemail| replace:: slurm@ganymede.utdallas.edu
.. |debugnodenum| replace:: 2

.. space limits
.. |homequota| replace:: 20 GB
.. |homemax| replace:: 30 GB
.. |homerectime| replace:: 7 Days
.. |scratchquota| replace:: None
.. |scratchmax| replace:: None
.. |scratchrectime| replace:: N/A

2 - Moving around |systemName|
//////////////////////////
Now that the user is logged in, lets navigate around |systemName| using Linux shell commands: 

2.1 - Linux Commands
********************
A basic knowledge of Linux commands is required to effectively use the |systemName| system. If you have basic knowledge of Linux Commands and Shell Scripting, feel free to skip this section. Note that a condensed version of useful Linux Commands can be found in Appendix A.

2.1.1 - Moving Around
---------------------
First, it is important to know where one is in the system in order to move around to desired directories (sometimes called folders).  The first function prints the working (current) directory. ::

  {pubssh:~/home} pwd
  /home/013/j/jx/jxw150830/home

The next step is to see what folders exist in the home directory, in order to know where to move around.  The fastest way to do this is to use ``ls``, the list command. ::

  {pubssh:~/home} ls
  Documents  Downloads  real.log

The list command has additional functionality that allows for long form to give more information about the files and folders that exist on the server by running ``ls -l``. ::

  {pubssh:~/home} ls -l
  total 4
  drwx--x--x+ 4 jxw150830 ee 5 May 21  2018 Documents
  drwx--x--x+ 2 jxw150830 ee 2 May 21 11:05 Downloads
  -rw-------+ 1 jxw150830 ee 0 May 21  2018 real.log

There are a couple of things worth noting.  The first set of letters show the permissions of the different files and directories.  In fact, the Linux environment treats everything as a file, with the only difference in the directory having the d on the first line.  Because of this, files can be saved with any extension of any length. 

Sometimes it is useful to see what is in another directory while not moving out of the current directory; this can be achieved by asking the list function to go somewhere else. ::

  {pubssh:~/home} ls Documents/
  Old-Photos  Research  Sample.txt

Now that possible directories to move into have been identified, the next step is to move into one.  This is done by changing the directory, or ``cd``.  ::

  {pubssh:~/home} cd Documents/
  {pubssh:~/home/Documents}

The next logical step is to list what items are in the directory. ::
  
  {pubssh:~/home/Documents} ls
  Old-Photos  Research  Sample.txt

Note that the only difference between this listing and the listing of this directory from before was that the user had to move to the directory to get the listing in the second case.

The next example will show how to move into a directory, list the contents, and then back out using the ``cd ..`` command. ::

  {pubssh:~/home/Documents} cd Research/
  {pubssh:~/home/Documents/Research} ls
  datafile.dat
  {pubssh:~/home/Documents/Research} cd ..
  {pubssh:~/home/Documents} ls
  Old-Photos  Research  Sample.txt

2.1.2 - Making Files and Directories
------------------------------------

Now that the user can move around, next is to make files and directories.  First, to create a new file in ``/home/Documents/Research``, we will move into ``/Research`` and create the file using the ``touch`` command. ::

  {pubssh:~/home/Documents/Research} touch project-day1
  {pubssh:~/home/Documents/Research} ls
  datafile.dat  project-day1

The ``touch`` command can also be used to create multiple files at a time, with or without file extensions. ::

  {pubssh:~/home/Documents/Research} touch project-day2 project-day3 bigdata.dat
  {pubssh:~/home/Documents/Research} ls
  bigdata.dat  datafile.dat  project-day1  project-day2  project-day3

The function to make directories, ``mkdir``, is very similar to ``touch``.  A single directory can be created, or multiple directories can be created if divided by spaces. ::

  {pubssh:~/home/Documents/Research} mkdir project\ files datafiles
  {pubssh:~/home/Documents/Research} ls -l
  total 4
  -rw-------+ 1 jxw150830 ee 0 May 21 11:48 bigdata.dat
  -rw-------+ 1 jxw150830 ee 0 May 21 11:37 datafile.dat
  drwx--x--x+ 2 jxw150830 ee 2 May 21  2018 datafiles
  -rw-------+ 1 jxw150830 ee 0 May 21 11:45 project-day1
  -rw-------+ 1 jxw150830 ee 0 May 21 11:48 project-day2
  -rw-------+ 1 jxw150830 ee 0 May 21 11:48 project-day3
  drwx--x--x+ 2 jxw150830 ee 2 May 21  2018 project files

Note that the "\\ " allows the user to define spaces in naming both files and directories.

2.1.3 - Moving Files and Directories
------------------------------------

Now that the user has created files and directories, it may be valuable to move them using the command ``mv``.  To begin, we will move the data files and project files into the appropriate directories.::

  {pubssh:~/home/Documents/Research} mv datafile.dat datafiles/
  {pubssh:~/home/Documents/Research} mv -t project\ files/ project-day1 project-day2 project-day3
  {pubssh:~/home/Documents/Research} ls -Rl
  .:
  total 4
  -rw-------+ 1 jxw150830 ee 0 May 21 11:48 bigdata.dat
  drwx--x--x+ 2 jxw150830 ee 3 May 21  2018 datafiles
  drwx--x--x+ 2 jxw150830 ee 5 May 21 13:09 project files

  ./datafiles:
  total 1
  -rw-------+ 1 jxw150830 ee 0 May 21 11:37 datafile.dat

  ./project files:
  total 2
  -rw-------+ 1 jxw150830 ee 0 May 21 11:45 project-day1
  -rw-------+ 1 jxw150830 ee 0 May 21 11:48 project-day2
  -rw-------+ 1 jxw150830 ee 0 May 21 11:48 project-day3

Note two things:  First is the change in the set up for doing one file ``mv <source> <destination>`` to ``mv -t <destination> <source1> <source2> <sourcenth>``.  The second is that the ``ls -R`` command allows the user to list recursively files and directories that are upstream of the current directory.

There is no specific command that is used for the renaming of files.  Instead, the user must move the file over itself with the new name.  In the following example, it will be assumed that the project-day files should have had the file extension .prj at the end. ::

 
  {pubssh:~/home/Documents/Research/project files} mv project-day1 project-day1.prj
  {pubssh:~/home/Documents/Research/project files} mv project-day2 project-day2.prj
  {pubssh:~/home/Documents/Research/project files} mv project-day3 project-day3.prj
  {pubssh:~/home/Documents/Research/project files} ls
  project-day1.prj  project-day2.prj  project-day3.prj

Moving directories is a very similar process to the moving of files. ::

  {pubssh:~/home/Documents/Research} mv project\ files/ datafiles/
  {pubssh:~/home/Documents/Research} ls -lR
  .:
  total 2
  -rw-------+ 1 jxw150830 ee 0 May 21 11:48 bigdata.dat
  drwx--x--x+ 3 jxw150830 ee 4 May 21  2018 datafiles

  ./datafiles:
  total 2
  -rw-------+ 1 jxw150830 ee 0 May 21 11:37 datafile.dat
  drwx--x--x+ 2 jxw150830 ee 5 May 21  2018 project files

  ./datafiles/project files:
  total 2
  -rw-------+ 1 jxw150830 ee 0 May 21 11:45 project-day1.prj
  -rw-------+ 1 jxw150830 ee 0 May 21 11:48 project-day2.prj
  -rw-------+ 1 jxw150830 ee 0 May 21 11:48 project-day3.prj

To move files to or from the |systemName| server, the use of secure copying is used, ``scp``.  The method below will detail how to move a file from the |systemName| server to the user's computer via the command line, but the process would be similar for data moving the other direction. ::

  {pubssh:~} scp ./gany.sh jxw150830@ganymede.utdallas.edu:/home/jxw150830/
  jxw150830@ganymede.utdallas.edu's password:
  gany.sh                                                    100%   51     0.1KB/s   00:00
  {pubssh:~}

The above example is moving information from a user's home folder on the server to the |systemName| home area.  Note that this process could go backwards as well.

Another tool that is useful for keeping items up to date through remote synchronization is ``rsync``.  The ``rsync`` command works to keep items up to date across multiple devices by updating information that has changed.  This method of keeping files up to date is more time efficient for large data sets where only minor changes are made; that is, *the changes, instead of the data set*, will be moved. ::

  {pubssh:~} rsync -avtr ./dataset/ jxw150830@ganymede.utdallas.edu:/home/jxw150830/
  jxw150830@ganymede.utdallas.edu's password:
  sending incremental file list
  ./
  data1.dat
  data2.dat
  data3.dat

  sent 203 bytes  received 72 bytes  36.67 bytes/sec
  total size is 0  speedup is 0.00
  {pubssh:~}

In the above example, each item is moved to |systemName|.  If the user does not want to see all of the files transferred, the user can remove ``-v``.  Similarly, the ``-r`` is the recursive command which will go down the folder structure to extract everything.  The ``-at`` should remain for file continuity.  If the user were to run the same command again, notice that a small amount of data was sent to check for updates, but the full files were not resent. ::

  {pubssh:~} rsync -avtr ./dataset/ jxw150830@ganymede.utdallas.edu:/home/jxw150830/
  jxw150830@ganymede.utdallas.edu's password:
  sending incremental file list

  sent 83 bytes  received 12 bytes  12.67 bytes/sec
  total size is 0  speedup is 0.00
  {pubssh:~}


2.1.4 - Removing Files and Directories
--------------------------------------

Often times files or directories are made in error or are no longer needed.  To remove an item, you use the remove tool ``rm``.  ::

  {pubssh:~/home/Documents/Research/datafiles} ls
  datafile.dat  project files
  {pubssh:~/home/Documents/Research/datafiles} rm datafile.dat
  rm: remove regular empty file `datafile.dat'? y
  {pubssh:~/home/Documents/Research/datafiles} ls
  project files

Remove will not let you remove a directory that has files in it.  With one or two files, removing them is not a time-consuming issue.  However, with nested directories, this can be a very time-consuming task to empty each level before removal.  This can be worked around, however, by using the command ``rm -r`` (for recursive). ::

  {pubssh:~/home/Documents/Research} rm datafiles/
  rm: cannot remove `datafiles/': Is a directory
  {pubssh:~/home/Documents/Research} rm -r datafiles/
  {pubssh:~/home/Documents/Research} ls
  bigdata.dat

2.1.5 - Viewing and Editing Files
---------------------------------

Now that the file and directory structure are in the right place, the user has multiple options for viewing and editing.
For viewing short files, simply using the ``cat <filename>`` command allows the user to see the file printed out in the command line. ::

  {pubssh:~/home/Documents} cat Sample.txt
  This is a sample Document
  This document has multiple lines
  
  {pubssh:~/home/Documents}

To view longer files, using the command ``cat <filename> | less`` allows the user to scroll through a long file.  Pressing the q key will release the user from the prompt.

For editing files there are multiple options.  The programs vim (https://www.vim.org/) and nano (https://www.nano-editor.org/) are popular projects that come fairly standard on most machines.  Beyond those, there are additional well documented programs out there that allow for the user to edit in the command line but explaining them is out of the scope of this document.

2.1.6 - Automating Commands
---------------------------

Many of the commands that have been executed, if needed to be executed over and over, would be very time consuming.  To allow for this sort of automation, including the option of user input, there is the shell script.   The bash shell script allows for the user to write programs that consist of other programs or commands that are build into the Linux environment.  The concept of this will be familiar to those users that are familiar with Matlab programming. 

Every shell script must have the file extension .sh and start with and have nothing else but the line: ``#! /bin/bash`` This is followed by the commands in the script.  The command ``echo`` is useful in scripts for printing out to the command line information about what is going on.  To run the script, run ``bash <script name>``. ::

  {pubssh:~/home/Documents} cat hw.sh
  #! /bin/bash
  # This is a comment and is useful
  echo " Hello World"
  {pubssh:~/home/Documents} bash hw.sh
    Hello World

The shell script can be a powerful tool, especially when variables are introduced.  There are two types of shell script input, those passed in the command line before hand and those begotten during the run process.
To put in input to the command line, follow this example. ::
 
  {pubssh:~/home/Documents} cat nameupfront.sh
  #! /bin/bash
  # This will get it upfront
  # from the user input
  echo "Your name is: $1"

  {pubssh:~/home/Documents} bash nameupfront.sh ganymede
  Your name is: ganymede
  
To get the input during runtime, the user can read in the value of variables. These variables can be named anything the user would like, and are reached with the ``$<varName>`` portion of the command. ::

  {pubssh:~/home/Documents} cat namelive.sh
  #! /bin/bash
  # This program asks during
  echo "What is your name? :"
  read name
  echo "Hello $name"

  {pubssh:~/home/Documents} bash namelive.sh
  What is your name? :
  ganymede
  Hello ganymede

::

2.2 - |systemName| Specific Instructions and Programs
**************************************************

2.2.1 - Environmental Variables
-----------------------------------------------

In |systemName|, there are specific environmental varables that are designed to save the user time.  The following table shows the variables with their respective equivalent values.

===================== =====================================
     Variable                   Equivalent Value
===================== =====================================
``$USER``             The user's NetID
--------------------- -------------------------------------
``$HOME``             ``/home/$USER``
--------------------- -------------------------------------
``$SCRATCH``          ``/petastore/ganymede/scratch/$USER``
===================== =====================================

These environmental variables are save the user time in typing locations.  Additionally, these can be used by the user in any shell script or command that is input. 

2.2.2 - Custom Programs
-----------------------------------

To save time, a command has been created to directly change the user's directory to the Scratch directory.  This command to change to scratch is ``cds``. ::

  [jxw150830@ganymede ~]$ pwd
  /home/jxw150830
  [jxw150830@ganymede ~]$ cds
  [jxw150830@ganymede jxw150830]$ pwd
  /petastore/ganymede/scratch/jxw150830
  [jxw150830@ganymedejxw150830]$ 



.. 2.2.3 - Special Instructions