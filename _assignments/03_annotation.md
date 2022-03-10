---
type: assignment
date: 2022-03-07T11:59:59+4:30
title: 'Programming Assignment #3 - Manual Data Annotation'
hide_from_announcments: false
due_event: 
    type: due
    date: 2022-04-01T11:59:59+4:30
    description: 'Programming Assignment #3 due'
---

# Learning Objectives

In this assignment, you will:

1. Perform manual annotation for a real-world NLP task (stance detection) to [see how the sausage is made](https://en.wiktionary.org/wiki/how_the_sausage_gets_made).
2. Compare annotations amongst group members and evaluate agreement using a measure of annotator agreement
3. Consider reasons why your annotations may have agreed or disagreed, and what this means for the potential limits of machine learning models, in particular those in natural language processing

Note: This assignment is the only one that will be the same for 474 and 574.

# Resources you can use to complete this assignment (a COMPLETE list)

**NOTE: You ARE allowed to use Google to find things that fit this list (i.e. it is often easy to google something like "plotly draw line graph" to find the right part of the plotly documentation).**

- Anything linked to in this assignment page
- Anything linked to from the course web page
- Any materials from another online course taught at a university (**if you use this, you MUST provide a link to the exact document used**)
- Anything posted by Kenny, Navid, or Yincheng on Piazza

# What to submit

1. Your annotations, in the format described below.
2. A PDF containing your responses to the questions below.
3. A python *script* (not a notebook!) containing code to a) compute annotator agreement, and b) for 574, to compare classifiers trained on the different annotator responses. 

# Assignment Details

**Note:** Because this assignment requires minimal coding, the entire assignment is specified on this webpage.

### Part 1: Performing Manual Annotation (60 points)

**Step 1. Download the data** You should first download your group's annotations from this website. To do so, visit https://kennyjoseph.github.io/cse474/static_files/pa3/&lt;YOUR_TEAM_NAME_LOWERCASED_SPACES_REPLACED&gt;.csv; which will lead you to a file that contains the annotations for your group. For example, if your team name was `EXAMPLE TEAM`, the tweets you will annotate are at [https://kennyjoseph.github.io/cse474/static_files/pa3/example_team.csv](https://kennyjoseph.github.io/cse474/static_files/pa3/example_team.csv). These CSVs contain 150 tweets in a two-column format. The first is a `Tweet_ID` (called `id`), a unique identifier for a tweet. The second is the `tweet_text` (called `text`), the content of the tweet. The final is a blank `label` column, just for expository purposes.

**Step 2. Think through the task a bit** Answer the following questions *before beginning annotation*! (I know, we can't make you, but you'll learn more if you do :) ).

*1.2.1 (2 points)* - Based on what we discussed in class about this dataset and the task of stance annotation (here, for attitudes towards vaccines), on what percent of the tweets that you annotate do you think the two annotators will agree? There is no right answer here, obviously, but provide a justification of your response.
*1.2.2 (3 points)* - Based on what we discussed in class about this dataset, what percent of the tweets that you annotate do you think will be labeled *pro-vaccine*? Justify your answer.

**Step 3. Split the data between annotators** You will need to make sure that each tweet is labeled by exactly two annotators, that each annotator labels exactly 100 tweets, and that all pairs of annotators share exactly 100 tweets together. **Note: For teams with only two people, you can each just label the same 100 tweets, and respond to 1.2.3 with "we only have two people".** The easiest way to do this is as follows:
- Annotator 1: Tweets 1-100
- Annotator 2: Tweets 51-150
- Annotator 3: Tweets 1-50 and 101-150

**Step 4. Do the annotation**  Once you have split the annotations, each of you should do your own annotations separately. The best thing to do is probably to use a google spreadsheet and have each of you perform the annotations in a separate tab. You should follow the following annotation scheme:
For each tweet, use one of three labels:
- **-1** if the you believe the person who wrote this tweet was, at the time of writing, *anti-vaccine* (against the idea of the vaccine and/or receiving the vaccine)
- **0** if you believe the person who wrote this tweet was, at the time of writing, totally neutral towards the vaccine
- **1** if the you believe the person who wrote this tweet was, at the time of writing, *pro-vaccine* (for the idea of the vaccine and/or receiving the vaccine)
- **X** if the tweet provides you with no information at all about this person's stance towards the vaccine.

**Step 5. Combine the annotations** Combine the annotations into a single file that contains 5 columns (or 4 if you are a team of 2 people) (**please make sure to include the column headers here**):
- `tweet_ID` - the unique ID of the tweet
- `annotator_1` - Stance labels from the first annotator ("first" is randomly selected amongst your group members) 
- `annotator_2` - Stance labels from the second annotator
- `annotator_3` - Stance labels from the third annotator (if one exists)
- `final_annotation` - The final agreed upon annotation (see Step 6 below)

**Note: obviously, there will be blanks in this file where annotators did not see a particular tweet.**

**Step 6. Finalize annotations (fill in the final_annotation column)** When the two annotators agree, fill this column in with the agreed upon label. When the two annotators disagree, a third team member should select amongst the two labels from the other team members for a final decision. If they disagree with both other annotators, then the team should discuss together. Alternatively, on teams of two, the two annotators should come to a consensus on the final label.

**Step 7. Write your file out for submission** Save a CSV of the completed annotation task and label it
`<YOUR_TEAM_NAME_LOWERCASED_SPACES_REPLACED>_annotations.csv`. We will grade this upon completion and both an automated and manual review of your annotations. This is worth 55 points on the assignment.


### Part 2 - Calculating Agreement (20 points)

Write a script entitled `calculate_agreement_<YOUR_TEAM_NAME_LOWERCASED_SPACES_REPLACED>.py` that does the following:

- Takes a filename in from the command line
- Reads in the file, which will be in the format specified in Step 5
- Calculates [Krippendorf's Alpha](https://en.wikipedia.org/wiki/Krippendorff%27s_alpha) for **nominal data**, as discussed in class. **Note: You should not use any pre-existing function for this, as I did in class, but the code for the class discussion should be helpful.**
- Calculates Percent agreement, as defined in class. **Note: You should not use any pre-existing function for this, as I did in class, but the code for the class discussion should be helpful.**
- Prints these two numbers out to standard out in the format `<KRIPPENDORFS_ALPHA_VALUE><TAB><PERCENT_AGREEMENT_VALUE>`

### Part 3 - Reflecting (20 points)

Please answer the following questions in your PDF (4 points each):

- *2.1* - What was your overall percent agreement, and how did this compare to your estimate from 1.2.1? Why were these similar/different?
- *2.2* - Was this annotation task harder or easier than you expected? Why, and what was the hardest part?
- *2.3* - Does this change your perspective on how people talk about health-related content on social media? Why or why not?
- *2.4* - What did you learn from this annotation task that will change your perceptions of how NLP models are trained moving forward?
- *2.5* - How do you think your team's agreement (say, in terms of Krippendorf's Alpha) will compare to the other teams? Why do you think so?
