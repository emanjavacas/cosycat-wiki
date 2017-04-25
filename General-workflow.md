# **General Workflow**

Cosycat is designed for easy use by students and researchers of various abilities and is versatile enought to be useful to a variety of kinds of research. The general pattern of work involves retrieving a set of data via regex query, filtering or sorting it for annotation, annotating the data and then conducting analysis upon the annotated set.

## **Query**

Queries are the system Cosycat uses to retrieve specified information from the files of the corpus. Cosycat queries use a standardised regex query system which defines the form and item to be retrieved in general terms and allows specification through the use of a variety of wild cards.

By entering a regex expression specifying a particular set of results, users can retrieve hits relevant to their investigation. These expressions can be specific, querying individual sentences or words, or more general, querying for a range of words, orthographical possibilities or structures using wildcards. Examples of queries used in MBG's research below along with descriptions of the intended target.

 * *(Insert example queries here)
 
The regex expressions can recognise any string of words and symbols (provided those symbols that are wildcards are 'escaped' first) and allows for underspecified items and alternatives. The more specific the query entered is, the less 'noise' will be retrieved in the results; the more general, the wider the scope will be, the query retrieving a wider range of possible results. Below find a list of useful, often used regex expressions.

 * *(Insert regex key here)
 
Queries are entered in the search box of the query pane.

### **Query Pane**

The query pane is the main window of Cosycat's research functions, allowing users to query the corpus, view retrieved hits in a paginated format, sort results, annotate queries, apply filters and change view settings. 

* *(Insert image here)

The query pane UI can be seen above: the interface is fairly straightforward with 5 primary elements as well as the menu bar. 

1. **Corpus Selection:** This dropdown menu selects the corpus to be queried from the list available to the application.

2. **Window and Size settings:** These dropdowns, as in the general settings menu, control the number of items around a hit in context (Window) and the number of hits per page (Size).

3. **Searchbox:** This textbox is used to enter and search the regex expression query.

4. **Pane-switch:** This button allows the user to switch between the query and annotation panes. When switched the panes are persistent, maintaining the status of hits, searches and marks.

5. **Annotation/pencil icon:** This icon allows a query to be annotated and saved for later use.

Once a search is conducted more options are revealed:

* *(insert image here)*

Here we see 6 further options, elucidated below:

1. **Sort Criterion:** This option opens a set of further options, allowing a user to select sort criteria for the hits of a query. The criteria options are: 
  * *:position*: match/left/right
  * *:attribute*: word
  * *:facet*: sensitive/insensitive
Multiple sort criteria can be applied to the same query through the use of the *+* button; the *-* button removes these sort functions.

2. **Pagination:** These options allow a user to move through the pages of results backward, foward and by specifying a page number.

3. **Filters:** The filter option controls the filters applied to the query, constraining its retrieval from the corpus to a set of data. Filters are actually automatically created based on the indexed structural attributes of the corpus (so, different corpora will have different filters). Below are example filters used by MBG in the EMMA corpus:
  * **Genre**
  * **textForm**
  * **Date**
  * **Generation**
  * **authorID**
  * **textID**
  * **docID**
  * **fromInputFile**
  * **title**
  * **author**
  * **translation**
  * **PTC**
  * *ADD FILTER DESCRIPTIONS*
Can be undone with the associated eraser button.

4. **Hide Hits:** Allows the user to select which hits should be hidden in the query pane results with the options of:
  * **None**
  * **Kept**
  * **Discarded**
  * **Unseen**
  * *(Add option descriptions)

5. **Prop:** (Add description text)

6. **Mark hits:** This button marks all the hits in the results currently viewed, selecting them to be carried over to the Annotation Pane. Can be undone with the associated eraser button.

## **Annotation Pane**
The annotation pane is the second window of Cosycat's primary research functions. It carries marked hits from the Query Pane to the annotation interface seen below.

* *(Insert image here)

Here there are 5 basic functions:

1. **Open:** Opens all the hits on the page, allowing their annotation interfaces to be accessed. (For details of annotation procedures, see the Annotation page). Hits can also be opened individually by clicking on the text line.

2. **Close:** Closes the open hits on the page.

3. **Snippet view:** Double clicking the hit number brings up a context snippet window, with expandable context for the hit in its text as well as source information.

4. **Pagination:** Scrolls through the pages of hits with an option for 'next', 'previous', 'first' and 'last' along with a page number readout.

5. **Pane Swap:** The pane swap button returns the user to the query pane.
