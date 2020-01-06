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

6 - Application Specific Instructions 
/////////////////////////////////////

There are certain programs that require users to run them by a specific method.  These can be added with modules as with other programs on the stack.

6.1 - Matlab
************

|systemName| currently has |matlabver| installed, and in addition to the site liscense there are |matlabdist| liscenses for distributed Matlab.  Matlab jobs can be run in 3 different ways: serial, parallel and distributed compute.  Each of these job types can either be batch or interactive.  The following sections will describe what this means to the user.

6.1.1 - Job Types
-----------------------

There are 3 different job types: Serial, Parallel Computing Toolkit, and Distibuted Compute Server.  

6.1.1.1 - Serial Jobs
+++++++++++++++++++++++++

Serial jobs are defined as jobs where one dataset exists in memory.  This can either be accessed by one processor or by multiple processors.  Serial jobs are created when a user runs standard Matlab scripts.

For an example of a serial job, the user can look in the directory ``/opt/ohpc/pub/examples/matlab/serial/`` and open the readme file.


6.1.1.2 - Parallel Computing Toolkit (PCT) Jobs
++++++++++++++++++++++++++++++++++++++++++++++++++

Parallel Computing Toolkit jobs are jobs that use openmp to call parallel processes using MPI.  These jobs follow directives that are established in the Matlab Parallel Computing Toolkit with full information available at https://www.mathworks.com/products/parallel-computing.html . The user has the availabity to run an instance of Matlab with each of the cores reserved in the current node.  |systemName| is equiped with |matlabsitenum| keys to ensure that many users can do parallel computing at once.
  
For an example of a serial job, the user can look in the directory ``/opt/ohpc/pub/examples/matlab/parallel/`` and open the readme file.

6.1.1.3 - Distributed Compute Server (DCS) Jobs
+++++++++++++++++++++++++++++++++++++++++++++++++

Distributed Compute Server jobs are very similar to PCT jobs, but these jobs leverage systems within Matlab to use multiple nodes to work on jobs instead of multiple instances as in PCT.  The user must use internal commands to Matlab to enable this, however Matlab automatically pulls the corret liscense type for the command run by the user.  The University currently owns |matlabdist| liscenses.  The default number that are run is 12, however the user can change the number of units run using the following code in their code: ::

  myCluster  = parcluster();
  poolobj = parpool(myCluster,32);


6.1.2 - Matlab Job Modes
--------------------------

Like all Slurm jobs, Matlab can either be run in the background with ``sbatch`` or interactively with ``srun``.  The user does, however, need to do some specific actions for matlab to work.

6.1.2.1 - Batch Jobs
+++++++++++++++++++++++++++

Using Slurm, an effecient way to run Matlab allows to user to set up a number of batches to run at the same time across multiple cores.  This means that if the user has the same program to run with multiple data sets, it is possible to batch the same program with multiple data sets.  This allows the system to run the multiple sets in tandem, yielding faster results.

To do this, the submission script needs to be stuctured like the one in Section 5.2.1 with the program section being replaced by ``matlab -nodisplay -nosplash <user function>.m << <input>``

6.1.2.2 - Interactive Matlab
++++++++++++++++++++++++++++++

Matlab can be run from an interactive terminal on a single compute node.  This is useful for users who want to tweak inputs as they go, or want to feed in live data.  See section 5.4 for how to log into a node.  Once logged in, the user needs to load the Matlab module. ::

  [jxw150830 ~]$ module load matlab

Once the user has added the module, executing `` `` will start matlab interactively.  This normally takes a few moments. ::

  [jxw150830 ~]$ matlab
  MATLAB is selecting SOFTWARE OPENGL rendering.
 
                            < M A T L A B (R) >
                  Copyright 1984-2018 The MathWorks, Inc.
                   R2018a (9.4.0.813654) 64-bit (glnxa64)
                             February 23, 2018

 
  To get started, type one of these: helpwin, helpdesk, or demo.
  For product information, visit www.mathworks.com.
 
  >> %%-- 06/04/18 01:33:51 PM --%%
  >> 

Once the Matlab terminal is loaded, the user can execute Matlab functions a usual.  When finished, the user should exit from the Matlab terminal and the compute node. ::

  >> exit
  [jxw150830 ~]$ exit
  exit
  [jxw150830 ~]$ 

.. 6.2 - Ansys

.. ***********
