# uGMRTprimarybeam
How to use the CASA task 'wbpbgmrt':
 - Keep the task_wbpbgmrt.py and wbpbgmrt.xml files in the same directory.
 - Start CASA in this directory.
 - At the CASA prompt give the command
   os.system('buildmytasks')
   It produces a few new files in this directory; one of which is 'mytasks.py'.
 - At the CASA prompt give the command
   execfile('mytasks.py')
   The task named wbpbgmrt is ready for use.
 - The command 'inp wbpbgmrt' at CASA prompt will show the inputs to this task.
 - vis = visibilities corresponding to the image which needs to be corrected for PB.
 - imagename = provide the prefix of the imagename.
 - chanlist = list of channel numbers across the band (see example below)
 - spwlist and weightlist are lists of the same length as chanlist. For GMRT spwlist is a list of zeros and weightlist is a list of 1s. (see example)
 - nterms = number of terms used in imaging with tclean/clean.
 - Example:
   Images with prefix "selfcal" are created by tclean from the MS file file.ms. file.ms has 200 channels and nterms= 2 was used in imaging.
   wbpbgmrt(vis = 'file.ms', imagename ='selfcal', nterms = 2,  action ='pbcor', chanlist =[10, 50, 100, 150, 190], spwlist =[0,0,0,0,0], weightlist=[1,1,1,1,1])
 - Please make sure that the correction is made as expected by checking the flux densities of some bright sources in your field spread over the full imaged area.
 - At the moment this task is being tested.
 - Please send your feedback or ask for help by writing to ruta@ncra.tifr.res.in.
# This task is a modification of the CASA task "widebandpbcor".
# Contributors to this modification: Ruta Kale, Biny Sebastian, D. V. Lal.
# The uGMRT primary beam parameters are from the report by D. V Lal and J. N. Chengalur that was released on 01Dec2018.
# Date: 18 June 2019.
