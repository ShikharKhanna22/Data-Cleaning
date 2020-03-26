# CS598: Theory and Practise of Data Cleaning - Final Project

## End-to-End Data Cleaning Workflow project implemented as a part of CS598 class at UIUC

## Project Goal
The following project aims at using the tools and techniques learned in the class to perform an end to end data cleaning on NYPL 
menu dataset. We have implemented following points:


### 1. Overview and initial assessment of the dataset (narrative and supplemental information). 

You should describe the structure and content of the dataset and quality issues that are apparent from an initial
inspection. You should also describe a (hypothetical or real) use case of the dataset and derive from it
some data cleaning goals that can achieve the desired fitness for use. In addition: Are their use cases
for which the dataset is already clean enough? Others for which it well never be good enough? You
can speculate a bit here – but the rest of the project should focus on a “middle of the road” use case that
requires a practically feasible amount of data cleaning.


### 2. Data cleaning with OpenRefine. 

In this first hands-on part of the project, you should use OpenRefine
to clean the chosen dataset—either (a) or (b) or your own (c)—as much as needed for the use case.
Document the result of this phase, both in narrative form and with supplemental information (e.g., which
columns were cleaned and what changes were made?). Can you quantify the results of your efforts? Also
provide provenance information from OpenRefine. Pay close attention to what OpenRefine includes and
does not include in its Operation History! If important information is missing in the latter, provide that
information in other ways.

### 3. Develop a relational database schema for your dataset. 

What logical integrity constraints (ICs) can you identify? Load the data into a SQLite database with your target schema. Use SQL queries to profile
the dataset and to check the ICs that you have identified!

### 4. Create a workflow model of your data cleaning workflow 

What are the key inputs and outputs of your workflow? What are the dependencies? Note: Here you may want to model the various steps you have
executed with OpenRefine as parts of the workflow. This way, the YesWorkflow model more clearly
describes what actually happened to what parts of the data. Create a visual version of your workflow
using the YesWorkflow tool. Supplementary material to help with YW will be posted on Piazza


# About the data

The New York Public Library is digitizing and transcribing its [collection of historical menus.](http://menus.nypl.org/) The collection includes about 45,000 menus from the 1840s to the present, and the goal of the digitization project is to transcribe each page of each menu, creating an enormous database of dishes, prices, locations, and so on. As of early June, 2017, the transcribed database contains 1,332,726 dishes from 17,545 menus.

This dataset is split into four files to minimize the amount of redundant information contained in each (and thus, the size of each file). The four data files are Menu, MenuPage, MenuItem, and Dish. These four files are described briefly here, and in detail in their individual file descriptions below.

### Menu
The core element of the dataset. Each Menu has a unique identifier and associated data, including data on the venue and/or event that the menu was created for; the location that the menu was used; the currency in use on the menu; and various other fields.

Each menu is associated with some number of _MenuPage_ values.

### MenuPage
Each MenuPage refers to the Menu it comes from, via the menu_id variable (corresponding to Menu:id). Each MenuPage also has a unique identifier of its own. Associated MenuPage data includes the page number of this MenuPage, an identifier for the scanned image of the page, and the dimensions of the page.

Each MenuPage is associated with some number of _MenuItem_ values.

### MenuItem
Each MenuItem refers to both the MenuPage it is found on -- via the menu_page_id variable -- and the Dish that it represents -- via the dish_id variable. Each MenuItem also has a unique identifier of its own. Other associated data includes the price of the item and the dates when the item was created or modified in the database.

### Dish
A Dish is a broad category that covers some number of MenuItems. Each dish has a unique id, to which it is referred by its affiliated MenuItems. Each dish also has a name, a description, a number of menus it appears on, and both date and price ranges.
