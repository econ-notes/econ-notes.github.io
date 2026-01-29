---
title: 'Project management: The master do file'
date: '2025-12-25'
---


The following is an example master do file used for a project.

```stata
/* 
This is the master do file for the project.

Author: 
Time: 
*/

*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>
*<> step 1. default setups
*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>

version 16

clear all
set more off
set maxvar 32767
set varabbrev off

*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>
*<> step 2. global macros to store folder paths
*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>

if "`c(username)'" == "name" global User "E:/project_path"

cd "${User}"

global Codes              "${User}/codes"
global Analysis           "${Codes}/analysis"
global Cleaning           "${Codes}/clean"
global Utilities          "${Codes}/util"

global Data               "${User}/data"
global RawData            "${Data}/a_raw_data"
global TempData           "${Data}/b_temp_data"
global FinalData          "${Data}/c_final_data"

global Output             "${User}/output"
global T01Results         "${Output}/T01_event_studies"

*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>
*<> step 3. libraries (user-written procedures) to be used 
*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>

*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>
*>> install all necessary packages to a local directory
*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>

/* do "${Utilities}/InstallPackages.do" */

*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>
*>> use packages stored in the local stata_libraries folder
*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>

/* 
net set ado "${user}/stata_libraries"

tokenize `"$S_ADO"', parse(";")
while `"`1'"' != "" {
    if `"`1'"'!="BASE" capture adopath - `"`1'"'
    macro shift
}
adopath ++ "${user}/stata_libraries"
*/

*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>
*<> step 4. set figure scheme 
*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>

grstyle clear
grstyle init
grstyle set plain, grid dotted
grstyle set size large: heading
grstyle set margin "0pt 0pt 0pt 10pt": heading
grstyle set size medlarge: axis_title
grstyle set color ebblue cranberry dkgreen
grstyle set color gray: histogram histogram_line

*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>
*<> step 5. replicate results in the paper
*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>*<>

*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>
*>> s-5-1. data cleaning
*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>*>>

global erase_temp_file = 1
    //&? 1 means that auxiliary dta files produced in the data cleaning and analysis process will be erased

/* 
capture log close 
log using "${Results}/2025logfile.txt", replace text

do "${Cleaning}/S0101_GenerateWorkerOutcomes.do"
do "${Cleaning}/S0102_GenerateHFMeasure.do"
do "${Cleaning}/S0201_GenerateWorkerOutcomes.do"
do "${Cleaning}/S0202_GenerateHFMeasure.do"

//&? It takes around 15 min to create all the main datasets used in the paper.
log close
*/
```
