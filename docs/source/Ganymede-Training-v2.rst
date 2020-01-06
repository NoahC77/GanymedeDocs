.. Changelog
   -----------------------------------------------------------------------
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



UTDallas HPC Cluster Users Guide
================================

.. contents:: Table of Contents

Acceptable User Guidelines
//////////////////////////
OIT CI Research Computing (OIT-CIRC) resources are deployed, configured, and operated to serve a large, diverse user community. It is important that all users are aware of and abide by OIT-CIRC Usage Policies. Failure to do so may result in suspension or cancellation of the project and associated allocation and closure of all associated logins. Illegal transgressions will be addressed through University of Texas at Dallas (UT-D) and/or legal authorities. See the :download:`Acceptable User Guidelines <AUG.pdf>` for more information.

Introduction
/////////////

**What is Ganymede:**

  |systemName| is a |nodecpunum| core cluster with |nodememnum| of memory based on Centos |centVer| / OpenHPC. It has a 10 Gigabit ethernet network and a QDR (40 Gbps) InfiniBand interconnect configured in a fat-tree topology. It has two distributed file systems, one for the home directories over the 10 Gigabit Ethernet network available via NFS and one for the work file system that is a 525 TB high-performance parallel file system (GPFS) accessible over the InfiniBand network. The GPFS file system uses Data Direct Networks (DDN) directly attached to InfiniBand storage for the back end hardware. Compute nodes are all dual processor with many core systems with a variety of Intel architectures including Sandy Bridge, Haswell and Broadwell. Additionally, several nodes in the system have Nvidia Quadro GPUs based on the Nvidia Kepler architecture.

**What is SLURM:** 

  Slurm is an open source, fault-tolerant, and highly scalable cluster management and job scheduling system for large Linux clusters. Slurm requires no kernel modifications for its operation and is relatively self-contained. As a cluster workload manager, Slurm has three key functions. First, it allocates exclusive to resources (compute nodes) to users for some duration of time so they can perform work. Second, it provides a framework for starting, executing, and monitoring work (normally a parallel job) on the set of allocated nodes. Finally, it arbitrates contention for resources by managing a queue of pending work.

**What is OpenHPC:**
  OpenHPC provides a collection of prebuilt software components common in HPC environments, such as provisioning tools, resource managers, I/O libraries, development tools, and a variety of scientific libraries. 
