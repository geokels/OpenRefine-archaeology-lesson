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
keypoints:
- "Removing leading and trailing whitespace from data can make for easier searching and sorting."
---

# Lesson

## Split


If data in a column needs to be split into multiple columns, and the parts are separated by a common separator (say a comma, or a space), you can use that separator to divide up the pieces into their own columns.


1. Let us suppose we want to split the `Authors` column into separate columns for First Name and for Last Name. 
2. Click the down arrow at the top of the `Authors` column. Choose `Edit Column` > `Split into several columns...`
3. In the pop-up, in the `Separator` box, enter a comma.
4. Uncheck the box that says `Remove this column`.
5. Click `OK`. You'll get some new columns called `Authors 1`, `Authors 2`, and so on.
6. Notice that in some cases `Authors 2` and `Authors 3` are empty. Why is this? What do you think we can do to fix this?

> ## Exercise
>
> Try to change the name of the second new column to "Authors". How can you correct the problem you encounter?
> 
> > ## Solution
> > 
> > On the `Authors 2` column, click the down arrow and then `Edit column` > `Rename this column`. Type "Authors" into the box
> > that appears. A pop-up will appear that says `Another column already named Authors`. This is because there is another column
> > where we've recorded all of the author names. You can choose another name like `Last Name` for this column or change the other 
> > `Authors` column you can change the name to `author_lname`.
> {: .solution}
{: .challenge}

## Undo / Redo

It's common while exploring and cleaning a dataset to discover after you've made a change that you really should have done something else first. OpenRefine provides `Undo` and `Redo` operations to make this easy.


1. Click where it says `Undo / Redo` on the left side of the screen. All the changes you have made so far are listed here, with the newest changes at the bottom of the list.
2. Click on the step that you want to go back to, in this case the previous step. The added columns will disappear.
3. Notice that you can still click on the last step and make the columns reappear, and toggle back and forth between these states. You can do this until you perform another action.
4. Leave the dataset in the state in which the `Authors` not yet split.

Important: If you skip this step, your solutions for later exercises will not be the same as shown in those exercise solutions.

## Trim Leading and Trailing Whitespace (Fix this exercise)

Words with spaces at the beginning or end are particularly hard for us humans to tell from strings without them, but the blank characters will make a difference to the computer. We usually want to remove these. OpenRefine provides a tool to remove blank characters from the beginning and end of any entries that have them.


1. In the header for the column `scientificName`, choose `Edit cells` > `Common transforms` > `Trim leading and trailing whitespace`.
2. Notice that the `Split` step has now disappeared from the `Undo / Redo` pane on the left and is replaced with a `Text transform on 3 cells`
3. Perform the same `Split` operation on `Authors` that you undid earlier. This time you should only get two new columns. Why?

> ## Solution
> 
> Removing the leading white spaces means that each entry in this column has exactly one space (between the genus and species names). 
> Therefore, when you split with space as the separator, you will get only two columns.
{: .solution}

Important: `Undo` the splitting step before moving on to the next lesson. If you skip this step, your solutions 
for later exercises will not be the same as shown in those exercise solutions.

