# Dynamically-Generated-Hate-Speech-Dataset
ReadMe for v0.2 of the Dynamically Generated Hate Speech Dataset from Vidgen et al. (2021). If you use the dataset, please cite our paper in the Proceedings of ACL 2021, and available on [Arxiv](https://arxiv.org/abs/2012.15761).
Contact Dr. Bertie Vidgen if you have feedback or queries: bertievidgen@gmail.com.

The full author list is: Bertie Vidgen (The Alan Turing Institute), Tristan Thrush (Facebook AI Research), Zeerak Waseem (University of Sheffield) and Douwe Kiela (Facebook AI Research). This paper is an output of the Dynabench project: https://dynabench.org/tasks/5#overall

## Dataset descriptions
v0.2.2.csv is the full dataset used in our ACL paper. 

v0.2.3.csv removes duplicate entries, all of which occurred in round 1. Duplicates come from two sources: (1) annotators entering the same content multiple times and (2) different annotators entering the same content. The duplicates are interesting for understanding the annotation process, and the challenges of dynamically generating datasets. However, they are likely to be less useful for training classifiers and so are removed in v0.2.3. We did not lower case the text before removing duplicates as capitalisations contain potentially useful signals.



## Overview
The Dynamically Generated Hate Speech Dataset is provided in one table.

'acl.id' is the unique ID of the entry.

'Text' is the content which has been entered. All content is synthetic.

'Label' is a binary variable, indicating whether or not the content has been identified as hateful. It takes two values: hate, nothate.

'Type' is a categorical variable, providing a secondary label for hateful content. For hate it can take five values: Animosity, Derogation, Dehumanization, Threatening and Support for Hateful Entities. Please see the paper for more detail. For nothate the 'type' is 'none'. In round 1 the 'type' was not given and is marked as 'notgiven'.

'Target' is a categorical variable, providing the group that is attacked by the hate. It can include intersectional characteristics and multiple groups can be identified. For nothate the type is 'none'. Note that in round 1 the 'target' was not given and is marked as 'notgiven'.

'Level' reports whether the entry is original content or a perturbation.

'Round' is a categorical variable. It gives the round of data entry (1, 2, 3 or 4) with a letter for whether the entry is original content ('a') or a perturbation ('b'). Perturbations were not made for round 1.

'Round.base' is a categorical variable. It gives the round of data entry, indicated with just a number (1, 2, 3 or 4).

'Split' is a categorical variable. it gives the data split that the entry has been assigned to. This can take the values 'train', 'dev' and 'test'. The choice of splits is explained in the paper.

'Annotator' is a categorical variable. It gives the annotator who entered the content. Annotator IDs are random alphanumeric strings. There are 20 annotators in the dataset.

'acl.id.matched' is the ID of the matched entry, connecting the original (given in 'acl.id') and the perturbed version.


For identities (recorded under 'Target') we use shorthand labels to constructed the dataset, which can be converted (and grouped) as follows:

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
	
## Code
Code was implemented using hugging face transformers library.




