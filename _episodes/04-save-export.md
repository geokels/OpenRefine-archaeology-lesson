---
title: "Exporting and Saving Data from OpenRefine"
teaching: 10
exercises: 5
questions:
- "How can we save and export our cleaned data from OpenRefine?"
objectives:
- "Save an OpenRefine project."
- "Export cleaned data from an OpenRefine project."
keypoints:
- "Cleaned data or entire projects can be exported from OpenRefine."
- "Projects can be shared with collaborators, enabling them to see, reproduce and check all data cleaning steps you performed."
---

# Lesson

## Saving and Exporting

In OpenRefine you can save or export an entire project, or a spreadsheet of the cleaned data. This means you're saving the data and all the information about the data cleaning and transformation steps you've done. By default, OpenRefine saves your project in its memory while you make changes to the data. If you close OpenRefine without exporting, you can still open it up again and see a list of your projects, then click on any one of them to open it up again. However, exporting your data or project allows it to be shared with others, stored elsewhere online or on your computer, and creates a record of the steps made to transform the original dataset.

## Exporting Cleaned Data 

To export just the cleaned data into a spreadsheet format:

1. Click `Export` in the top right and select the file type you want to export the data in. `Tab-separated values` (`tsv`) or `Comma-separated values` (`csv`) would be good choices.
2. That file will be exported to your default `Download` directory. That file can then be opened in a spreadsheet program or imported
into programs like R or Python.

### Exporting Your Project

Exporting a project is also helpful, for instance, if you wanted to send your raw data and cleaning steps to a collaborator, 
or share this information as a supplement to a publication. To export a project:

1. Click the `Export` button in the top right and select `Export project`.
2. A `tar.gz` file will download to your default `Download` directory. The `tar.gz` extension tells you that this is a compressed file.
Which means that this file contains multiple files. You can double-click on the `tar.gz` file and it will expand into a directory. A 
folder icon will now appear. 
3. Look at the files that appear in this folder. What files are here? What information do you think these files contain?

> ## Solution
> You should see:
> - a  `history` folder which contains three `zip` files. Each of these files itself contains a `change.txt` file. 
> These `change.txt` files are the records of each individual transformation that you did to your data. 
> - a `data.zip` file. When expanded, this `zip` file includes a file called `data.txt` which is a copy of your raw data.
> You may also see other files.
{: .solution}

You can import an existing project into OpenRefine by clicking `Open...` in the upper right > `Import Project` and selecting the `tar.gz` project file. This project will include all of the raw data and cleaning steps that were part of the origina project.

