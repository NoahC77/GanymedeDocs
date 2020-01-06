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

1 - Connecting to |systemName|
//////////////////////////

It is important to note that the individual nodes can only be accessed after the user has logged into the |systemName| node, and have a running job on compute nodes.

1.1 - Microsoft Windows
***********************
Once the user's account has been created the user can access |systemName| using multiple Secure Shell (SSH) terminal software such as:

- PuTTY
- Bitwise
- MobaXterm  

This guide is written from the prospective that the user is connected to the UT Dallas network.  If the user is working outside of the UT Dallas network, follow the VPN guide at https://www.utdallas.edu/oit/vpn/ or to connect via the command line the SSH guide at https://www.utdallas.edu/oit/howto/create-an-ssh-connection/  to connect to the campus securely.

1.1.1 - PuTTY:
--------------
PuTTY for the Microsoft Windows environment can be installed by going to www.putty.org. Download and install the latest version of Putty. 

.. image:: ./assets/1.1.1-1.png

Once running PuTTY, in the Host Name section type **CBsysname.utdallas.edu**.  Go down to the saved sessions section, name the server with a meaningful name (in this case |systemName|) and press save.  By doing this, time can be saved in the future by clicking your particular saved session and pressing load.  Once loaded into the host name, click on the open button. 

.. image:: ./assets/1.1.1-2.jpg

A Putty Security Alert window will open for the first time prompting you for a Yes/No/Cancel answer to the question of saving a new host key. Click the Yes button and now you will be asked for login-id and password. Your login-id is your UTD NetID and your password is the same as your UTD NetID password.

.. image:: ./assets/1.1.1-3.png

1.1.2 - Bitvise:
-----------------
Bitvise can be installed by going to https://www.bitvise.com/index and pressing the download tab across the top banner.  Press the first option, **Download Bitvise SSH Client (Tunnelier)** the press **Bitvise SSH Client Installer** and follow the instructions for to install the software. Similar to PuTTY, the Host Name section type **CBsysname.utdallas.edu**.  Go down to the "Save profile as" button, name the file with a meaningful name (in this case |systemNameLower|.tlp) and press save.  By doing this, time can be saved in the future by clicking "Load profile".  Once loaded into the host name, click on the Login button.

.. image:: ./assets/1.1.2.png

1.1.3 - MobaXTerm:
-------------------
MobaXterm can be installed from http://mobaxterm.mobatek.net/download.html. The program can be demo-ed from site http://mobaxterm.mobatek.net/demo.html. 

To login, type ``ssh <NetID>@ganymede.utdallas.edu``. Once logged in, all of the available Linux files and directory information will be displayed on the left white pane. Within the MobaXterm interface, one can securely copy files between Linux and Windows desktops.  To open a file, right click on it and choosing option "open with default text editor". Changes can then be made to a file and the changes can then be saved. 

.. image:: ./assets/1.1.3.png

1.2 - For Mac Users
*****************************
For MAC users MobaXterm is not available.  Install XQuartz from https://www.xquartz.org. Additionally, the user could use terminal application as an SSH terminal client. 

1.3 - For Linux Users
**********************
For Linux users, the ssh command is built into the operating system.  To connect to the |systemName| server, open the terminal agent and type: ``ssh <NET-ID>@ganymede.utdallas.edu.``

1.4 - Mailing List
*********************

Another way for users to connect to |systemName| is to connect with other users.  The admin team has set up a mailing list that can allow users to interact with each other and find solutions through searchable archives.  Because the admins are members of the group, timely answers and solutions pass through the group.  The users should think of this as an additional form of documentation to reference.  This list can be accessed at |mailinglistaddr|.

