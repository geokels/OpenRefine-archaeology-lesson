---
title: "Working with OpenRefine"
teaching: 15
exercises: 10
questions:
- "How can we find and correct errors in our raw data?"
- "How can we separate our data?"
objectives:
- "Manipulate data using previous steps with undo/redo."
- "Employ drop-downs to split values from one column into multiple columns."
- "Employ drop-downs to remove white spaces from cells."
- "Parse data by utilizing a regular expression."
keypoints:
- "Removing leading and trailing whitespace from data can make for easier searching and sorting."
- "Parsing data using regular expressions, which can be simple or complex, can remove unwanted text quickly."
---

# Lesson

## Split


If data in a column needs to be split into multiple columns, and the parts are separated by a common separator (say a comma, or a space), you can use that separator to divide up the pieces into their own columns.

Insert screenshot here.

1. Let us suppose we want to split the `Authors with Affiliations` column into separate columns for each Author and their Affiliation. 
2. Click the down arrow at the top of the `Authors with Affiliations` column. Choose `Edit Column` > `Split into several columns...`
3. In the pop-up, in the `Separator` box, enter a semi-colon.
4. Uncheck the box that says `Remove this column`.
5. Click `OK`. You'll get some new columns called `Authors with Affiliations 1`, `Authors with Affiliations 2`, and so on.

> ## Exercise
>
> Try to change the name of the second new column to "Authors". How can you correct the problem you encounter?
> 
> > ## Solution
> > 
> > On the `Authors with Affiliations 2` column, click the down arrow and then `Edit column` > `Rename this column`. Type "Authors" into > > the box that appears. A pop-up will appear that says `Another column already named Authors`. This is because there is another column
> > where we've recorded all of the author names. You can choose another name like `Author Affiliation` or `author_affiliation` for this > > column.
> {: .solution}
{: .challenge}

## Undo / Redo

It's common while exploring and cleaning a dataset to discover after you've made a change that you really should have done something else first. OpenRefine provides `Undo` and `Redo` operations to make this easy.


1. Click where it says `Undo / Redo` on the left side of the screen. All the changes you have made so far are listed here, with the newest changes at the bottom of the list.
2. Click on the step that you want to go back to, in this case the previous step. The added columns will disappear.
3. Notice that you can still click on the last step and make the columns reappear, and toggle back and forth between these states. You can do this until you perform another action.
4. Leave the dataset in the state in which the `Authors with Affiliations` is not split.

Important: If you skip this step, your solutions for later exercises will not be the same as shown in those exercise solutions.

## Trim Leading and Trailing Whitespace

Words with spaces at the beginning or end are particularly hard for us humans to tell from strings without them, but the blank characters will make a difference to the computer. We usually want to remove these. OpenRefine provides a tool to remove blank characters from the beginning and end of any entries that have them.


1. In the header for the column `Authors with Affiliations`, choose `Edit cells` > `Common transforms` > `Trim leading and trailing whitespace`.
2. Notice that the `Split` step has now disappeared from the `Undo / Redo` pane on the left and is replaced with a `Text transform on # cells`
3. Perform the same `Split` operation on `Authors with Affiliations` that you undid earlier. 

Important: If you skip this step, your solutions for later exercises will not be the same as shown in those exercise solutions.

## Add Column Based on This Column


If specific data in a column needs to be parsed out from the rest of the data in a column, you can use the OpenRefine feature called "Add Column Based on This Column" which will allow you to use simple language, or more complex language, to create a new column with the desired data.

> ## Exercise
> 1. Let us suppose we want to parse the `Authors with Affiliations` columns we created earlier so that only the author's affiliation is
> listed. 
> 2. Click the down arrow at the top of the `Authors` column. Choose `Edit Column` > `Add Column Based on This Column...`
> 3. In the pop-up, in the `New Column Name` box, enter author_institution.
> 4. Copy/paste the below text into the available box (this text is called a [regular expression](https://librarycarpentry.github.io/lc-data-intro/04-regular-expressions/)):
>
> `import re
>  pattern = re.compile(r"((university|college|institute).+?),", re.I)
>  list = []
>  for i in pattern.findall(value):
>  list.append(i[0])
>  return ":::".join(list)`
>  
> 5. In the dropdown menu, select the option that says `Python/Jython`.
> 6. Click `OK`. You'll get some new columns called `author_institution 1`, `author_institution 2`, and so on.
> 7. Notice that in some cases there are multiple affiliations listed in the same cell. Why is this? What do you think we can do to fix this?
>
> > ## Solution
> > 
> > The regular expression that we used searches for specific keywords and then parses or "pulls" out the text surrounding those 
> > keywords. This means that if an author listed more than one affiliation, the expression will pull all of them out of the original
> > text and join them back together in the new column we created. 
> > Let's move onto the next lesson, where we discuss Faceting and Clustering, to find out how we can fix this issue.
> {: .solution}
{: .challenge}
