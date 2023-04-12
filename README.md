# CMU Energy Expert Finder Documentation
This dashboard finds experts who are faculty affiliates at the Wilton E. Scott Institute for Energy Innovation (Carnegie Mellon University) by searching research topics. 

03/01/2023

by Wilton E. Scott Institute for Energy Innovation and University Libraries, Carnegie Mellon University

## Data source
The CMU Energy Expert Finder (EF hereafter) relies on the [Dimensions](https://www.dimensions.ai/) database that curates various kinds of scholarly data (e.g., publication, grant, dataset). Currently, EF shows results for two types of data separately: publication and grant. For both these types of data, EF collects the most recent 10 years of scholarly records that the current faculty affiliates at the Wilton E. Scott Institute for Energy Innovation (Scott Institute hereafter) contribute to.

## Usage restriction
Because EF retrieves its data using the [Dimensions Analytics API](https://docs.dimensions.ai/dsl/api.html#api-access), which is a subscription-based product made available by the University Libraries at Carnegie Mellon University (CMU hereafter), only individuals affiliated with CMU have access to the tool.

## Concept and concept score
The core search ability of EF relies on Dimensions’ [concept](https://docs.dimensions.ai/dsl/language.html#searching-using-concepts). To quote the Dimensions documentation: <b>“Concepts are noun-phrases automatically extracted from a document’s abstract as well as the rest of the Dimensions database, which is used to weight their importance and relevance within the document’s field of study. For instance, the phrases machine learning and neural network will be considered very relevant in a computer science paper, while project and study will have their relevance scores low as they are generic phrases.”</b>

When user searches a research topic (e.g., “air quality”), EF will find all the scholarly records that contain the concept “air quality,” and the records that have concepts containing the term “air quality” (e.g., “indoor air quality”).

Dimensions also assigns a relevance score to a concept (i.e., concept score). Concept score is defined as the relevance of a given concept to the discipline of a publication (or grant). This score ranges from 0 to 1. A high value means that a concept is highly relevant to a certain discipline. For example, aluminum alloy can be mentioned in a history paper and in a materials science paper. The concept score helps distinguish between these two cases. Dimensions uses machine learning to decide, based on its large body of textual data, that aluminum alloy may tend to be more relevant to material science rather than history from a disciplinary perspective.

## Fields of research
In Dimensions, the discipline of a scholarly record is referred to as field of research ([FoR](https://plus.dimensions.ai/support/solutions/articles/23000018826-what-is-the-background-behind-the-fields-of-research-for-classification-system-)). This is a classification system sourced from the Australian and New Zealand Standard Research Classfication (ANZSRC). A single record can have multiple FoRs.

## How to use
Users start by entering any research topic in the text box, then click the "Search" button. Any concepts that contain the input text will be matched. Publications or grants that contain matched concepts and contributed by the current faculty affiliates at the Scott Institute will be returned. 

### Main Results
#### Bar graph
The associated concept scores (y-axis) will be plotted against expert names (x-axis) in a bar graph, so that users can see which experts focus more on some matched concepts than on others. If an expert has multiple matched concepts, or a single concept can be found in multiple records associated with this expert, the results will be stacked along the y-axis for this expert.

#### Collaboration networks
Two collaboration networks are shown. One treats author as node, and the other treats a CMU entity (e.g., department, school, college, etc.) as node. The legend under each network provides instructions on interpreting the networks.

### Interactive features
1. A slider for specifying a year range for the displayed results;
2. Two tabs under the search box for switching between publication and grant;
3. A slider for specifying a range of concept scores for the displayed results;
4. Users can interact with the bar graph using the standard features provided by [plotly](https://plotly.com/python/bar-charts/) (e.g., hovering mouse over the bars to see the exact concept scores and selecting/deselecting the matched concepts in the legend);
5. A checklist to select (or deselect) certain fields of research. The fields are based on the 2-digit classification level in ANZSRC);
6. there is also a button to show or hide the returned publication or grant data. To keep the interface clean, the default is to hide the publication or grant data. However, if needed, users can choose to see more information about a publication or grant (e.g., abstract). Users can enter text to filter a column. Finally, the results can be downloaded (in CSV) using the “Export” button.

## Data update
The data is updated once a week in the backend, provided that the faculty list is up to date.

To update the faculty list for EF, there are two relevant Excel files in the `\data` folder:
* name_org.xlsx
* name_researcher_id.xlsx

Contact staff at the Scott Institute for the most recent lists.

For Scott Institute staff, update `name_org.xlsx` and `name_researcher_id.xlsx` in the following ways:

1. `name_org.xlsx` is a file that connects each expert with this expert's official affiliations at CMU. The input in the second column should be strictly standardized. Multiple affiliations are seperated by ", " (<b>that is, comma AND a space</b>). Also, "and" should be used instead of "&". All major words are capitalized.
2. `name_researcher_id.xlsx` is a file that connects each expert with this expert's researcher ID in the Dimensions system. To find an expert's researcher ID, go to `https://app.dimensions.ai/discover/publication`, then on the left, click "RESEARCHER" -> "More" -> then type the expert name. If found, click on the name. Then, click "Limit to". The research ID can be found in the URL address box of your browser. At the end of the URL, look for the part that starts with "ur." Sometimes, judgments need to be made to see whether an expert is associated with multiple researcher IDs in Dimensions. If this is the case, in `name_researcher_id.xlsx`, put these IDs together in the same cell and separate them by ", " (<b>again, comma AND a space</b>). It is also possible that a researcher ID is missing for an expert in Dimensions. If this is the case, just leave the cell empty.  

## Acknowlegments
This project was completed by Luling Huang during his position at the Scott Institute and the University Libraries at CMU as a Council on Library and Information Resources (CLIR) postdoctoral fellow in energy social science data curation. This fellowship is made possible in partnership with CLIR, with the generous support of the Alfred P. Sloan Foundation. This fellowship has been supervised by Rikk Mulligan (Digital Scholarship Strategist, University Libraries), as well as former and current Scott Institute leadership (Anna Siefken, Daniel Tkacik, Jay Whitacre).

Many thanks to Jonathan Kiritharan (Web & Applications Developer, University Libraries) who provided data structure consultation and set up EF on a University Libraries’s server, David Scherer (former Scholarly Communications and Research Curation Consultant, University Libraries) who provided Dimensions support at CMU, and Aiswariya Raja (former Research Associate, Scott Institute).  