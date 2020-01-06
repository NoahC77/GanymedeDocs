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
3 - |systemName| Space Constraints
//////////////////////////////

One of the important considerations in High Performance Computing is the amount of space that is allocated to each user.  The |systemName| cluster is space allocated to provide the maximum amount of space while still providing desirable attributes to the cluster user.

3.1 - Types of Space
********************

There are currently 2 types of space available to the user, home space and scratch space. Home space is located in the ``/home/$USER`` folder and the scratch folder is located in the ``/petastore/ganymede/scratch/$USER`` folder. For convenience, the scratch folder is symbolically linked inside the user's home folder in ``/home/$USER/scratch`` The following table compares the attributes of the two available spaces.

+------------+-------------------+-----------------------+
| Attributes |     Home Space    |     Scratch Space     |
+============+===================+=======================+
| Purpose of | To house scripts, | To have a large area  |
| the Space  | source code and   | for working with data |
|            | output data.      | or trying ideas       |
+------------+-------------------+-----------------------+
| Backed Up  |        Yes        |           No          |
+------------+-------------------+-----------------------+


3.2 - Space Policies
********************

In addition to the attributes listed above, there are space considerations that need to be addressed due to limited storage.  Each of the users must stay within a certain quota. Should the quota be exceeded, the user will be warned by the following statement : ``dm-0: warning, user block quota exceeded.``  The user will not loose data, but instead is given a short period of time to comply to the block quota.  If the user runs a process that exceeds the Hard Limit, then the process will be stopped and the user will get the following error : ``dm-0: write failed, user block limit reached.``  The following table compares the different space limitations that exist on the particular 

+------------------+---------------+------------------+
| Attributes       |   Home Space  |   Scratch Space  |
+==================+===============+==================+
|   Hard Limit     | |homequota|   | |scratchquota|   |
+------------------+---------------+------------------+
|   Soft Limit     | |homemax| [*]_| |scratchmax| [*]_|
+------------------+---------------+------------------+
| Days to Comply   | |homerectime| | |scratchrectime| |
+------------------+---------------+------------------+

.. [*] The scratch space is located in ``/petastore/ganymede/scratch/$USER`` but does not count against the storage in the home space, even with the symbolic link.

.. [*] While the petabyte storage device is not metered, the scratch space should be cleaned up when a project is finished to ensure that there is enough room for others interested in using the space.


3.3 - Checking Available Space
******************************

The user should be aware of the amount of free space that is remaining, in order to ensure that the user does not run out of space for data during a run of a program or module.  In order to check the amount of space, the user needs to check the ``quota``. ::

  [jxw150830@ganymede~]$ quota -s
  Disk quotas for user jxw150830 (uid 532471):
       Filesystem   space   quota   limit   grace   files   quota   limit   grace
  /dev/mapper/volgroup0-lvolexport
                      44K  20000M  30000M              11       0       0

In the case above, the entire 20 GB is available to be used.  After running a couple of processes, the ``/home`` space is filled above the quota. ::

  [jxw150830@ganymede~]$ quota -s
  Disk quotas for user jxw150830 (uid 532471):
       Filesystem   space   quota   limit   grace   files   quota   limit   grace
  /dev/mapper/volgroup0-lvolexport
                   22529M* 20000M  30000M   6days      13       0       0

Note that the number of days in the grace period will slowly go down until the user is out of compliance completely.  At this point, if the amount of time runs out, the user will no longer be able to write new data until they move below the |homequota| threshold.  If at any point the user goes above |homemax|, the user will immediately loose the ability to write until the ``/home`` directory is brought back into compliance.
