# mb1-analysis/metadata

This folder contains a series of csvs that are referenced by the analysis scripts to deal with a variety of issues that need to be dealt with on a case-by-case basis. Wherever possible, lab-by-lab and subject-by-subject changes or notations are included here, so that they can be checked and updated in an error-minimizing way. Where applicable, these descriptions include information about whether the data in the csv file were created specifically for MB1B or taken from MB1 files.

TODO: If you know what each of these files is, please describe it! Use the following template:

### unconfirmed_unmatched_participants.csv

DESCRIPTION: A programmatically generated file that summarizes participants who are absent from either the trials or the participant-level data, along with some informative columns. This is intended to help guide by-hand identification of the remaining data cleaning issues (circa 8/28/18). 
REFERENCED AT: About line 307 of `01_read_and_merge.Rmd`

### true_unmatched_participants.csv

TODO: this file needs to be examined and edited for mb1b (all info in this file is currently from mb1)

DESCRIPTION: A by-hand marking of participants determined to be not fixable by merge/typo stuff, and what to do about this.  This includes mainly 3 things: Pilot participants (but not all of them), subject numbers that are in sequence, but never corresponded to a kid, and subject numbers that DID correspond to a kid, typically one who went on to complete 0 trials of the experiment. About line 250 of `01_read_and_merge.Rmd`

### ManyBabiesQuestionnaireSpreadsheetAuthoritativeMay22-2018cleaned.csv - ManyBabiesQuestionnaireMay22-2018cleaned.csv.csv

### NAE_labs.csv

DESCRIPTION: This .csv file lists labs for which the primary language of the lab location is North American English. US English and CAN English are both treated as North American English. File was taken over from MB1, but labs who are not part of MB1B were removed from the file. 
REFERENCED AT: approx. line 669 of `02_variable_validation.Rmd`

### Variable_Dictionary_mb1.csv

DESCRIPTION: This .csv contains information about each of the variables including whether the variable is at the participant or lab level, the source of the variable, variable name, unit of measurement for the variable, possible values for the variable (as suggested in data entry instructions, though these weren't used by all labs), a brief explanation of the variable, and whether or not the variable will be included in the Lab Factors paper. This file was created for MB1 and has not been changed at all for MB1B. 
REFERENCED AT: not referenced 

### labs_convert_looking_time_to_seconds.csv

DESCRIPTION: This .csv lists labs who reported looking time in milliseconds. We determined whether labs reported looking time in milliseconds by examining their trials data – labs for which the majority of trial lengths seems excessively long for reporting in seconds (e.g., most trial length values around or above 1000) were classified as having reported trial length in milliseconds and were thus marked for conversion in this metadata file. Related to issue # 11 in mb1 repo. File was taken over from MB1, but labs who are not part of MB1B were removed from the file. 
REFERENCED AT: line 783 of `02_variable_validation.Rmd`

### labs_trim_looking_time_to_18s.csv

DESCRIPTION: This .csv file lists all of the labs who had any number of participant trials with looking times over 18s (which should not be possible given that the max stimulus length is 18s). Per meeting on 10/19/18 we have decided to trim all looking times to 18s. However, this metadata file contains information about why looking times were over 18s for each lab. For some labs, long looking times were between 18s and 19s, so these are likely just minor timing issues in the stimulus presentation program. Other reasons for stimuli longer than 18s are specified in the `reasons` column and described further in issue #216 in MB1 repo. This file was not modified for MB1B. However, all looking times for MB1B that are greater than 18s are also under 20s which we ignored in MB1 as they seem like minor timing issues. 
REFERENCED AT: originally referenced at approx. line 762 of `02_variable_validation.rmd` in MB1 analysis (but we have now decided to clip ALL files at 18s so now there is no reference to this file in the code).

### participants_cog_hearing_exclusions.csv

DESCRIPTION: This .csv file lists participants who were originally coded as excluded for having vision, hearing, or cognitive developmental issues but that we felt were  appropriate to actually include (i.e., an infant who has a minor eye infection or parents with vision issues). Justifications for deciding whether to include these participants can be found in issue #16.

Issues classified as:
1. minor vision/eye issue - issues (such as a minor eye infection or the infant is farsighted) that seem unlikely to influence infants' performance in the current study.
2. family history - cases in which the parent reports a family history of vision issues or autism, but these issues are with individuals other than the infant.
3. physical delay - cases in which the parent reports a physical delay (e.g., not yet crawling) that seems unlikely to influence infants' performance in the current study.
4. parental concerns - concerns reported by parents (e.g., sometimes the infant doesn't respond right away or the infant seems small for their age) that seem unlikely to influence infants' performance in the current study.
5. true exclusion - infant has major vision / hearing / developmental issues that do warrant exclusion from the current study.

This file contains both information for MB1 and MB1B (only 2 participants in the file are in MB1B analyses.)

REFERENCED AT: line 424 in `02_variable_validation.Rmd`

### participants_columns_used.csv

DESCRIPTION: A .csv file generated by approx. lines 50-60 in `01_read_and_merge.Rmd`. In the first column, this file lists all of the column names that are used in any of the data files that have been read in. The second column lists either the name of the file in which this column name is used or, if it is used in more than 1 file, the value is "many." This is later used for remapping column names (see `participants_columns_remapping` below). This file is generated by in the code and is thus unique to MB1B.
REFERENCED AT: line 64 in `01_read_and_merge.Rmd`

### participants_columns_remapping.csv

DESCRIPTION: A .csv file that maps the names of columns used in data files that have been read in to more consistent column names for the ManyBabies analyses. This file was created by examining the `participants_columns_used` file and manually entering the values that they should be mapped to. The column labeled `column` lists the column values from `participants_columns_used`. The column labeled `status` indicates whether the column should be included, excluded, or substituted (sub) in the data file that results from using this file. If `status` = `sub`, the `substitution` column indicates what to sub for that column name. The `type` column specifies the data type. The `file` column again lists either the name of the file in which this column name is used or, if it is used in more than 1 file, the value is "many." This file was generated specifically for MB1B, but is very similar to the file in MB1.
REFERENCED AT: line 70 of `01_read_and_merge.Rmd`

### participants_session_error_fussiness.csv

TODO: this file needs to be examined and edited for mb1b (all info in this file is currently from mb1)

DESCRIPTION:  A .csv file that lists participants that were excluded by a lab for "global fussiness". We either do not have detailed trial-level error information about these babies (i.e. on which particular trials they were fussy) or we do not have any trial data for these participants. See issue #57 and #186 for detailed discussion.
REFERENCED AT: not currently referenced

Columns:
lab: the lab's unique ID (formatted to match the IDs post pre-processing)
subid: the participant's unique ID (formatted to match the IDs post pre-processing)
fussiness_kind: an explanation of the reason the participant is included in the file
trials_recoded_as_error: whether trials needed to be recoded as an error for the participant 

### participants_session_error_keep.csv

DESCRIPTION: A .csv file that lists participants we have identified as being incorrectly classified as a session error. See issue #57 (in MB1) and #21 (in MB1B) for detailed discussion. The file version in this repo was created specifically for MB1B.
REFERENCED AT: Approx. line 565 in `02_variable_validation`.

Columns:
lab: the lab's unique ID (formatted to match the IDs post pre-processing)
subid: the participant's unique ID (formatted to match the IDs post pre-processing)
session_error_recoded: whether the session error will be recoded (for flexibility)
session_error_change_reason: a short description of the reason the session error is recoded 

### participants_session_error_type.csv

DESCRIPTION: A .csv file that lists participants we have identified as session errors along with a unified/ consistent coding of their session error type (since labs varied greatly in the way they used the column session_error_type). The file version in this repo was created specifically for MB1B.
REFERENCED AT: Approx. line 585 in `02_variable_validation.Rmd` and 112 in `paper/exclusions.Rmd`.

Columns:
lab: the lab's unique ID (formatted to match the IDs post pre-processing)
subid: the participant's unique ID (formatted to match the IDs post pre-processing)
session_error_type_recoded: the session error type (equipment failure, experimenter error or outside interference)

### participants_trial_error_update.csv

TODO: this file needs to be examined and edited for mb1b (all info in this file is currently from mb1)

DESCRIPTION: A .csv file that lists trials we have identified as being incorrectly classified as a trial error or incorrectly classified as not being a trial error. See issue #107 (and #19 and #57) for detailed discussion.
REFERENCED AT: Approx. line 623 in `02_variable_validation.Rmd`

Columns:
lab: the lab's unique ID (formatted to match the IDs post pre-processing)
subid: the participant's unique ID (formatted to match the IDs post pre-processing)
trial_error_recoded: whether the trial will be recoded (for flexibility)
trial_error_new: the new coding of the trial (error or noerror)
trial_error_change_reason: a short description of the reason the trial error is recoded

### preterm_fix.csv

DESCRIPTION: A .csv file that lists either: (a) the number of weeks each lab used as full term or (b) indicates that all infants in a given lab's data are full term. Used to edit the `days_preterm` column so that it reflects days less than 37 weeks for all labs. File was taken over from MB1, and still includes information about labs who are not part of MB1B. 
REFERENCED AT: Approx. line 480 in `02_variable_validation.Rmd`

### columns_used_in_02_variable_validation.csv 

DESCRIPTION: A .csv file that lists which columns are read into the `02_variable_validation.Rmd` file. This .csv also contains information about the variable types that were used to read in each column and which columns are available but were dropped when reading in the file since they're not used in analyses.
REFERENCED AT: `columns_used_in_02_variable_validation` is mentioned in comment on line 59 of `02_variable_validation.Rmd`

### columns_used_in_analyses.csv 

DESCRIPTION: A .csv file, simliar to the one described above, the lists which columns are read in and used in analyses (e.g., all files after `02_variable_validation.Rmd`). This file lists the column type for each column that was read in as well as columns that were available from the output of `02_variable_validation.Rmd` but were dropped because they are not necessary for analyses.
REFERENCED AT: `columns_used_in_analyses` is mentioned in a comment on line 9 of `paper/exclusions.Rmd`; line 37 of `04_merge_with_monolinguals.Rmd`