# Helis Academy Pathway Analysis Practical
==============================================================================
## January 2021
Practical prepared by Dr. Martina Summer-Kutmon and Dr. Lauren J. Dupuis

-------------------------------------------------------------------------------------------------------------------------
<br>
Pathway analysis helps you to interpret the data in a biologically meaningful context. We will use the data from the paper “Identification 
of a novel biomarker, SEMA5A, for non-small cell lung carcinoma in nonsmoking women“ by Lu et al. published in Cancer Epidemiology, 
Biomarkers & Prevention in 2010 (see [paper](https://cebp.aacrjournals.org/content/19/10/2590.long)). You will need the WikiPathways human pathways collection that you can download [here](http://www.wikipathways.org/wpi/batchDownload.php?species=Homo%20sapiens&fileType=gpml&tag=Curation:AnalysisCollection) as a 
zip file. You will need to unzip it before use. You will also need the BridgeDb identifier mapping file for humans which you can download [here](https://bridgedb.github.io/data/gene_database/).

For this assignment, you will the data file comp_LungCancer-Normal.txt from the repository.

## Assignment 1: Open a Pathway in PathVisio
---------------------------------------------

Begin by starting PathVisio. Open the Cell Cycle pathway from the WikiPathways collection you downloaded.
* Go to File → Open → Browse → Go to the folder with the Human pathways 
* Select Hs_Cell_Cycle_WP179_103430.gpml

> Small numbers above data nodes, interactions or the info box in the top left of the pathway indicate publication references. 
> Double click the *info box in the top left* (Title, Availability, Last modified, Organism) and go to the “Literature” tab. 
> There you can determine if there is a paper reference for this pathway.

> Click on the GSK3B gene in the top left. Check the “Backpage” tab on the right side to determine which identifier and database the gene is annotated with. 

**Load the identifier mapping database:** 
1.	Go to Menu Data → Select Gene Database → Browse to Hs_Derby_Ensembl_91.bridge in the Data folder
2.	Check the status bar at the bottom to see if the gene database has been loaded correctly. 

>Click on the GSK3B gene again and go to the “Backpage” tab to see if you can now also find other identifier(s) for this gene.  


## Assignment 2: Data Import in PathVisio
-------------------------------------------

> Open the statistical analysed data in Excel (comp_LungCancer-Normal.txt in Pathway_Analysis_Data folder). The first column 
> contains the identifier of the genes (ENSG_ID). From which of the three database below are the identifiers in the dataset? 
> *(Required for following steps!)*
>
> - [ ]    Ensembl
> - [ ]    Entrez Gene
> - [ ]    OMIM

Import the data as described below. Go through the different dialogs. 

Steps data import:
1.	Menu “Data” → Import expression Data
2.	Select the lung cancer dataset (comp_LungCancer-Normal.txt in the Data folder in the private Github repository) as the input file. Everything else 
should be filled in automatically (see Figure 2a).
3.	In the next dialog, make sure the correct separators are used. You should see the different columns in the preview (see Figure 2b).

![Figure 2A and 2B](https://github.com/LaurenDupuis/Helis-Academy-Omics-June-2019/blob/master/images/Figure_2A_2B_PA.png?raw=true)


4.	Important: in the next step you need to select the column that contains the gene identifier and the database (system code) for 
the identifier. Select the database you chose in question 2A (Note: if the database is wrong your identifiers will not be recognized 
correctly), see Figure 2c. 
5.	Now the data is imported (see Figure 2d). **Before clicking “Finish”** answer the questions below:

![Figure 2C and 2D](https://github.com/LaurenDupuis/Helis-Academy-Omics-June-2019/blob/master/images/Figure%202C_2D_PA_.png?raw=true)

> How many rows were successfully imported?

> How many identifiers were not recognized?  
> **Important:** if the number of rows is the same as the number of identifiers not recognized the data import was not done correctly - 
> you probably didn’t select the correct database (step 4 data import)! Redo the import or ask one of the instructors for help. 
> **(Required for following steps!)**

### **Check before you continue!**
If you clicked finish, you should see a default visualization on the pathway (if all genes are gray, the data import was not 
successful → please redo the import, make sure you select the correct database in step 4, otherwise ask one of the instructors). 
Click on the GSK3B gene and check the “Data” tab on the right side → do you see the expression data?
-----------------------------------------------------------------------------------------------------------------------------------

## Assignment 3: Creating a Basic Visualization
Follow the instruction to create a basic visualization:

1.	Go to Data → Visualization Options
2.	Create a new visualization named “basic visualization”

![Figure 3A](https://github.com/LaurenDupuis/Helis-Academy-Omics-June-2019/blob/master/images/Data_Vis_1_PA_.png?raw=true)


3.	Select “Expression as color” and “Text label”. 
4.	In “Expression as color” select “Basic”.
5.	Check the checkbox before “logFC” and define a new color set.

![Figure 3B](https://github.com/LaurenDupuis/Helis-Academy-Omics-June-2019/blob/master/images/Data_Vis_2_PA_.png?raw=true)

6.	Select “Gradient” and define a gradient from -1 over 0 to 1 (blue - white - red) → Click OK.

![Figure 3C](https://github.com/LaurenDupuis/Helis-Academy-Omics-June-2019/blob/master/images/Data_Vis_3_PA_.png?raw=true)


> *Consider what the colors in the pathway mean biologically* (Hint: Check the “Legend” tab 
> on the right side). 

> Select the ORC6 gene (bottom left), go to the “Data” tab. What is the logFC of the ORC6 gene?

## Assignment 4: Create and Advanced Visualization
PathVisio also allows users to visualize multiple data columns together. For that we need to create a new advanced visualization.

1.	Go to Data → Visualization Options
2.	Create a new visualization named “advanced visualization”
3.	Select “Expression as color” and “Text label”. 
4.	In “Expression as color” select “Advanced”.
5.	Check the checkbox before “LogFC” and define a new color set, see Figure 3a.
6.	Select “Gradient” and define a gradient from -1 to 0 to 1 (blue - white - red) → Click OK (same as in simple visualization).
7.	Check the checkbox before “P.Value” and define a new color set, see Figure 3b.
8.	At the bottom, click on “Add Rule”. Go to the text field next to “Rule Logic” and specify the following criteria: [P.Value] < 0.05. Then click on color and select a light green. Click OK and OK, see Figure 3c. 

![Figure 4](https://github.com/LaurenDupuis/Helis-Academy-Omics-June-2019/blob/master/images/Fig4.png?raw=true)

> Consider what the colors in the different columns on the data nodes in the pathway mean 
> biologically by checking the “Legend” tab on the right side. 

-------------------------------------------------------------------------------------------------------

## Assignment 5: Perform Pathway Statistics

To identify pathways that might be affected by lung cancer, you can perform pathway statistics to calculate Z-Scores for each pathway (check lecture!). PathVisio automatically ranks the pathways based on the Z-Score. 

1.	Go to Menu Data → Statistics
2.	First we need to define a criteria for differentially expressed genes. We are going to select those genes based on significant p-value but we are also going to make sure the change is high enough by specifying a logFC threshold:
    a.	([logFC] < -1 OR [logFC] > 1) AND [P.Value] < 0.05

> Consider what this expression criteria means (which genes will be selected)?
> ([logFC] < -1 OR [logFC] > 1) AND [P.Value] < 0.05

3.	Now we need to specify the pathway directory. Find the directory: 
Wikipathways-Human-Pathways. If you need to download the human pathway collection, you can do so [here](http://data.wikipathways.org/20210110/gpml/wikipathways-20210110-gpml-Homo_sapiens.zip).
4.	Browse to this directory and select it. 
5.	Then click on Calculate and wait for the result table.

> Observe the top altered pathways and their Z-Scores. Do you see highly ranked pathways in the result 
> table that you expect to be affected by lung cancer?

> How many genes of the dataset are in at least one pathway (N) and how many differentially expressed genes of the 
> dataset are present in at least one pathway (R)? (Check “N and R" above the result table)

> What is the pathway with the lowest Z-Score? What does a low Z-Score mean biologically? (ignore pathways with NaN)



