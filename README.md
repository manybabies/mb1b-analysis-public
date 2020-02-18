# mb1b-analysis

This repository contains the data and code for the project ManyBabies 1B: Infant-Directed Speech Preference in Bilingual Infants. Materials related to the project can be found on OSF https://osf.io/zauhq/.  Additional details can be found in the related ManyBabies 1 (monolingual) OSF page: https://osf.io/re95x/ and repository: https://github.com/manybabies/mb1-analysis-public

## Description of main analysis scripts (in root directory)

These scripts should be run in order in the case of any data modification

01_read_and_merge.Rmd: Reads in bilingual participants and trials datasets, and merges them
02_variable_validation.Rmd: Validates all variables used in the analyses
03_exclusion.Rmd: Implements exclusion criteria.  Participant-level exclusions is done via a call to /paper/exclusions.Rmd . This is because we need to detail all of the participant level exclusion in the paper itself. This script also removes training trials and short looking times
04_merge_with_monolinguals.Rmd: Reads in cleaned monolingual dataset from mb1 github repo, and merges with bilinguals
05_confirmatory_analysis.Rmd: Implements confirmatory analysis
06_exploratory_analysis.Rmd: Implements exploratory analysis 

The final analysis is contained within the paper itself:

/paper/mb1b-paper.Rmd


## Follow-up analyses
The data and code are licensed for re-use. To coordinate with other interested parties, we suggest following the three steps.

Identify the research question you want to pursue. If you are not sure whether the dataset contains the information you would need or whether the relevant analysis is already in the works, feel free to email manybabies-gb@mailman.stanford.edu to ask about it.

Compose a brief email to send to this list (manybabies1@lists.stanford.edu) explaining your idea, and provide a mechanism for other ManyBabies1 contributors to sign up/express interest. Be sure to describe what kinds of contributions you are looking for. If there are particular skill-sets you are especially looking for, it’s a good idea to mention these in the email. Christina Bergmann recently sent a good example of such an email, in which she called for a comparison of MB1 to meta-analysis.

Make sure you communicate clearly about what constitutes authorship level contribution (and how authorship will be structured) and expected timelines for completion of the project. This can evolve as the project does, as long as there is agreement and clarity.

## Citation policy
As courtesy, we ask that publications cite the manuscript describing the project and main results:

Byers-Heinlein, K., et al. (2019). A multi-lab study of bilingual infants: Exploring the preference for infant-directed speech. Registered report with in principle acceptance. *Advances in Methods and Practices in Psychological Science.*
