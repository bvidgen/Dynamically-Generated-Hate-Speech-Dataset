# Dynamically-Generated-Hate-Speech-Dataset
ReadMe for v0.1 of the Dynamically Generated Hate Speech Dataset from Vidgen et al. (2020). If you use the dataset, please cite our paper on Arxiv.
Contact Dr. Bertie Vidgen if you have feedback or queries: bertievidgen@gmail.com.
Please note that this is v0.1 of the dataset. Updates may be released in the future.

The full author list is: Bertie Vidgen (The Alan Turing Institute), Tristan Thrush (Facebook), Zeerak Waseem (University of Sheffield) and Douwe Kiela (Facebook). This paper is an output of the Dynabench project: https://dynabench.org/tasks/5#overall


## Overview
The Dynamically Generated Hate Speech Dataset is provided in two tables.

The first table is the dataset of entries, with the entry ID, label, type, annotator ID, status, round, split, round model predictions and whether the model was fooled (model_wrong).

The second table is the targets of the hate, in a wide format. Because annotators could identify targets inductively, a large number were identified with only or two associated entries, often if they were intersectional characteristics. We combine all identities mentioned in fewer than 15 entries into an 'Other category'. This affects less than 1% of all the hateful entries, whilst reducing the number of target identities to 41. The two tables can be merged on the 'ID' variable.


## Table 1: Dataset of entries
'id' is the unique ID of the entry.

'text' is the content which has been entered. All content is synthetic, although it might in some cases be closely inspired by real world hate and non-hate.

'label' is a binary variable, indicating whether the content hs been identified as hate or not.

'type' is a categorical variable, providing a secondary label for hateful content. For hate t can take five values: Animosity, Derogation, Dehumanization, Threatening and Supoprt for Hateful Entities. Please see the paper for more detail. For non-hate 'type' is always NA. Note that in round 1 a type was not given. You can subset to only round 1 if you want to account for this (see 'round').

'model_wrong' is a logical variable. It reports whether the taarget model for that round was fooled. Note that models were retrained and redployed in between each round, which means that the model_wrong value can only be understood in relation to each round.

'db.model_preds' gives the model prediction, from 0 (not hate) to 1 (hate). As with 'model_wrong' it can only be understood in relation to each round. Note that model predictions are not available for entries completed offline without a model-in-the-loop, i.e. the perturbation rounds.

'status' reports whether the entry is original content entered into Dynabench or a perturbation. See the paper for more information. 

'round' is a categorical variable. It gives the round of data entry, indicated with a number (1, 2 or 3) and then a letter for whether the entry is original content entered into Dynabench ('a') or a perturbation ('b'). Perturbations were not made for round 1. As such 'round' can take the values: 1, 2a, 2b, 3a and 3b.

'split' is a categorical variable. it gives the data split that the entry has been assigned to. This can take the values 'train', 'dev' and 'test'. The choices of splits is given in the paper.

'annotator' is a categorical variable. It gives the annotator who entered the content. Annotator IDs are random alphanumeric strings. There are 20 annotators in the dataset.


## Table 2: Dataset of targets
'id' is the unique ID of the entry. It can be used to merge the dataset with the other table.

All entries assigned to 'non hate' have 'none' as a target.
Hateful entries assigned to 'hate' are associated with 41 distinct target identities.

Any identities with 8 or fewer entries were combined into an 'Other' category. This reduced the number of target identities, whilst only affecting 1% of the data (see the paper for more details).

One other variable is important to note: 'NoTargetRecorded'. This is for entries which were entered without a target identity at the point of creation (i.e. all entries in Round 1 and a small number, erroneously, from the subsequent rounds.)

Note that for the 'Supporting hateful entities' type of hate the target identified is the entity which is being supported. Specifically, the dataset includes 'Nazi' and 'Hitler', with the other entities being listed in 'Other'.

We use shorthand labels for targets when constructing the dataset, which can be converted (and grouped) as follows:

	none -> for non hateful entries 
	NoTargetRecorded -> for hateful entries with no target recorded
	
	mixed -> Mixed race background
	ethnic minority -> Ethnic Minorities
	indig -> Indigenous people
	indigwom -> Indigenous Women
	non-white -> Non-whites (attacked as 'non-whites', rather than specific non-white groups which are generally addressed separately)
	trav -> Travellers (including Roma, gypsies)

	bla -> Black people
	blawom -> Black women
	blaman -> Black men
	african -> African (all 'African' attacks will also be an attack against Black people)
	
	jew -> Jewish people
	mus -> Muslims
	muswom -> Muslim women

	wom -> Women	
	trans -> Trans people
	gendermin -> Gender minorities, 
	bis -> Bisexual
	gay -> Gay people (both men and women)
	gayman -> Gay men
	gaywom -> Lesbians	
	
	dis -> People with disabilities
	working -> Working class people
	old -> Elderly people

	asi -> Asians
	asiwom -> Asian women
	east -> East Asians
	south -> South Asians (e.g. Indians)
	chinese -> Chinese people
	pak -> Pakistanis
	arab -> Arabs, including people from the Middle East

	immig -> Immigrants
	asylum -> Asylum seekers
	ref -> Refguees
	for -> Foreigners
	
	eastern european -> Eastern Europeans
	russian -> Russian people
	pol -> Polish people
	hispanic -> Hispanic people, including latinx and Mexicans

	nazi -> Nazis ('Support' type of hate)
	hitler -> Hitler ('Support' type of hate)
	





