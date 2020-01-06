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

Appendices
//////////

Appendix A - Linux Commands
***************************

============================ ===============================================
          Command                               Usage
============================ ===============================================
pwd                          print current directory
---------------------------- -----------------------------------------------
ls                           list contents
---------------------------- -----------------------------------------------
ls -l                        list longform
---------------------------- -----------------------------------------------
cd                           change to home directory
---------------------------- -----------------------------------------------
cd [directory path]          change to directory
---------------------------- -----------------------------------------------
mkdir                        make a directory
---------------------------- -----------------------------------------------
touch                        create a file
---------------------------- -----------------------------------------------
mv [source] [destination]    move a file or directory
---------------------------- -----------------------------------------------
rm [file]                    remove a file or directory
---------------------------- -----------------------------------------------
cat [file]                   view a file (non-editable)
---------------------------- -----------------------------------------------
scp                          secure copy
---------------------------- -----------------------------------------------
rsync                        secure copy, only writes data that has changed
---------------------------- -----------------------------------------------
ssh                          create secure shell connection to a remote host
---------------------------- -----------------------------------------------
ssh -X                       create ssh connection with X-window forwarding
============================ ===============================================

Appendix B - Slurm Commands
***************************

Man pages exist for all Slurm daemons, commands, and API functions. The command option --help also provides a brief summary of options. Note that the command options are all case sensitive.

**sacct**
  sacct is used to report job or job step accounting information about active or completed jobs.

**salloc** 
  salloc is used to allocate resources for a job in real time. Typically this is used to allocate resources and spawn a shell. The shell is then used to execute srun commands to launch parallel tasks.

**sattach**
  sattach is used to attach standard input, output, and error plus signal capabilities to a currently running job or job step. One can attach to and detach from jobs multiple times.

**sbatch**
  sbatch is used to submit a job script for later execution. The script will typically contain one or more srun commands to launch parallel tasks.

**sbcast**
  sbcast is used to transfer a file from local disk to local disk on the nodes allocated to a job. This can be used to effectively use diskless compute nodes or provide improved performance relative to a shared file system.

**scancel**
  scancel is used to cancel a pending or running job or job step. It can also be used to send an arbitrary signal to all processes associated with a running job or job step.

**scontrol**
  scontrol is the administrative tool used to view and/or modify Slurm state. Note that many scontrol commands can only be executed as user root.

**sinfo**
  sinfo reports the state of partitions and nodes managed by Slurm. It has a wide variety of filtering, sorting, and formatting options.

**smap**
  smap reports state information for jobs, partitions, and nodes managed by Slurm, but graphically displays the information to reflect network topology.

**squeue**
  squeue reports the state of jobs or job steps. It has a wide variety of filtering, sorting, and formatting options. By default, it reports the running jobs in priority order and then the pending jobs in priority order.

**srun**
  srun is used to submit a job for execution or initiate job steps in real time. srun has a wide variety of options to specify resource requirements, including: minimum and maximum node count, processor count, specific nodes to use or not use, and specific node characteristics (so much memory, disk space, certain required features, etc.). A job can contain multiple job steps executing sequentially or in parallel on independent or shared resources within the job's node allocation.

**strigger**
  strigger is used to set, get or view event triggers. Event triggers include things such as nodes going down or jobs approaching their time limit.

**sview**
  sview is a graphical user interface to get and update state information for jobs, partitions, and nodes managed by Slurm.
