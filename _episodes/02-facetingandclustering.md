---
title: "Faceting and Clustering in OpenRefine"
teaching: 10
exercises: 10
questions:
- "How can we convert a column from one data type to another?"
- "How can we visualize relationships among columns?"
- "How can we sort and summarize our data?"
objectives:
- "Recall what facets are and how they are used to sort and summarize data."
- "Recall what clustering is and how it is applied to group and edit typos."
- "Transform a text column into a number column."
- "Identify and modify non-numeric values in a column using facets."
- "Use scatterplot facet to examine relationships among columns."
keypoints:
- "OpenRefine also provides ways to get overviews of numerical data."
- "Faceting and clustering approaches can identify errors or outliers in data."
---

# Lesson

## Text Faceting

*Exploring data by applying multiple filters*

OpenRefine supports faceted browsing as a mechanism for

* seeing a big picture of your data, and
* filtering down to just the subset of rows that you want to change in bulk.

Typically, you create a facet on a particular column. The facet summarizes the cells in that column to give you a big picture of that column, and allows you to filter to some subset of rows for which the cells in that column satisfy some constraint. That's a bit abstract, so let's jump into some examples. 

[More on faceting](https://github.com/OpenRefine/OpenRefine/wiki/Faceting)

Here we will use faceting to look for potential errors in data entry in the `scientificName` column.

1. Scroll over to the `scientificName` column.
2. Click the down arrow and choose `Facet` > `Text facet`.
3. In the left panel, you'll now see a box containing every unique value in the `scientificName` column 
along with a number representing how many times that value occurs in the column.
4. Try sorting this facet by name and by count. Do you notice any problems with the data? What are they?
5. Hover the mouse over one of the names in the `Facet` list. You should see that you have an `edit` function available. 
6. You could use this to fix an error immediately, and OpenRefine will ask whether you want to make the same correction to every value it finds like that one. But OpenRefine offers even better ways to find and fix these errors, which we'll use instead. We'll learn about these when we talk about clustering.

> ## Solution
> 
> There will be several near-identical entries in `scientificName`. For example, there is one entry for `Ammospermophilis harrisi` and
> one entry for `Ammospermophilus harrisii`. These are both misspellings of `Ammospermophilus harrisi`. We will see how to correct these 
> misspelled and mistyped entries in a later exercise.  
{: .solution}

> ## Exercise
>
> 1. Using faceting, find out how many years are represented in the census.  
>
> 2. Is the column formatted as Number, Date, or Text? How does changing the format change the faceting display?
>
> 3. Which years have the most and least observations?
> 
> > ## Solution
> > 
> > 1. For the column `yr` do `Facet` > `Text facet`. A box will appear in the left panel showing that there are 26 unique entries in
> > this column.  
> > 2. By default, the column `yr` is formatted as Text. You can change the format by doing `Edit cells` > `Common transforms` > 
> > `To number`. Doing `Facet` > `Numeric facet` creates a box in the left panel that shows a histogram of the number of 
> > entries per year. Notice that the data is shown as a number, not a date. If you instead transform the column to a date, the 
> > program will assume all entries are on January 1st of the year.   
> > 3. After creating a facet, click `Sort by count` in the facet box. The year with the most observations is 1997. The least is 1977. 
> > 
> {: .solution}
{: .challenge}

## Clustering

In OpenRefine, clustering means "finding groups of different values that might be alternative representations of the same thing". For example, the two strings `New York` and `new york` are very likely to refer to the same concept and just have capitalization differences. Likewise, `Gödel` and `Godel` probably refer to the same person. Clustering is a very powerful tool for cleaning datasets which contain misspelled or mistyped entries. OpenRefine has several clustering algorithms built in. Experiment with them, and learn more about these algorithms and how they work. 

1. In the `scientificName` Text Facet we created in the step above, click the `Cluster` button.
2. In the resulting pop-up window, you can change the `Method` and the `Keying Function`. Try different combinations to 
 see what different mergers of values are suggested.
3. Select the `key collision` method and `metaphone3` keying function. It should identify three clusters. 
4. Click the `Merge?` box beside each, then click `Merge Selected and Recluster` to apply the corrections to the dataset.
4. Try selecting different `Methods` and `Keying Functions` again, to see what new merges are suggested. You may find there are 
 still improvements that can be made, but don't `Merge` again; just `Close` when you're done.  We'll now 
 see other operations that will help us detect and correct the remaining problems, and that have other, more general uses.

Important: If you `Merge` using a different method or keying function, or more times than described in the instructions above, 
your solutions for later exercises will not be the same as shown in those exercise solutions.

[More on clustering](https://github.com/OpenRefine/OpenRefine/wiki/Clustering-In-Depth)

## Numbers

When a table is imported into OpenRefine, all columns are treated as having text values. We saw earlier how we can sort column values as numbers, but this does not change the cells in a column from text to numbers. Rather, this interprets the values as numbers for the purposes of sorting but keeps the underlying data type as is. We can, however, transform columns to other data types (e.g. number or date) using the `Edit cells` > `Common transforms` feature. Here we will experiment changing columns to numbers and see what additional capabilities that grants us.

Be sure to remove any `Text filter` facets you have enabled from the left panel so that we can examine our whole dataset. You can remove an existing facet by clicking the `x` in the upper left of that facet window.

To transform cells in the `recordID` column to numbers, click the down arrow for that column, then `Edit cells` > `Common transforms…` > `To number`. You will notice the `recordID` values change from left-justified to right-justified, and black to green color.

> ## Exercise
>
> Transform three more columns, including `period`, from text to numbers. Can all columns be transformed to numbers?
> 
> > ## Solution
> > 
> > Only observations that include only numerals (0-9) can be transformed to numbers. If you apply a number transformation to 
> > a column that doesn't meet this criteria, and then click the `Undo / Redo` tab, you will see a step that starts with 
> > `Text transform on 0 cells`. This means that the data in that column was not transformed.
> > 
> {: .solution}
{: .challenge}

### Numeric facet
Sometimes there are non-number values or blanks in a column which may represent errors in data entry and we want to find them. 
We can do that with a `Numeric facet`.

> ## Exercise
>
> 1. For a column you transformed to numbers, edit one or two cells, replacing the numbers with text (such as `abc`) or blank (no number or text).
> 2. Use the pulldown menu to apply a numeric facet to the column you edited. The facet will appear in the left panel.
> 3. Notice that there are several checkboxes in this facet: `Numeric`, `Non-numeric`, `Blank`, and `Error`. Below these are counts of the number of cells in each category. You should see checks for `Non-numeric` and `Blank` if you changed some values.
> 4. Experiment with checking or unchecking these boxes to select subsets of your data.
{: .challenge}

When done examining the numeric data, remove this facet by clicking the `x` in the upper left corner of its panel. Note that this does not undo the edits you made to the cells in this column. If you want to reverse these edits, use the `Undo / Redo` function.

## Scatterplot facet

Now that we have multiple columns representing numbers, we can see how they relate to one another using the scatterplot facet. Select a numeric column, for example `recordID`, and use the pulldown menu to > `Facet` > `Scatterplot facet`. A new window called `Scatterplot Matrix` will appear. There are squares for each pair of numeric columns organized in an upper right triangle. Each square has little dots for the cell values from each row.

> ## Exercise
>
> 1. Examine the scatterplots overall. Do the patterns make sense?
> 2. Why does the scatterplot for `recordID` vs `period` have the pattern it does?
{: .challenge}

## Examine pair of columns in detail

We can examine one pair of columns by clicking on its square in the `Scatterplot Matrix` A new facet with only that pair will appear in the left margin. 

> ## Exercise
>
> Click in the scatterplot facet in the left margin and drag to highlight a rectangle. This will subset the data to those entries.
{: .challenge}

> ## Exercise
> 
> - Click on the `Scatterplot Matrix` square for `recordID` and `period` to get that as a facet in the left margin.
> - Redo the `Text filter` on `scientificName` to show only entries including the letters `bai`.
> Notice the change in the scatterplot. It might be easier to see if you click `export plot` to put it on a new browser tab.
{: .challenge}
