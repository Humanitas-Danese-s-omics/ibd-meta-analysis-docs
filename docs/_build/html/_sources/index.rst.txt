.. TaMMA documentation master file, created by
   sphinx-quickstart on Fri Apr 23 15:27:36 2021.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

.. image:: https://ibd-meta-analysis.herokuapp.com/assets/logo.png
  :alt: IBD TaMMA logo

.. toctree::
   :maxdepth: 2
   :caption: Contents:

Welcome to IBD TaMMA's documentation
======================================

What's the goal ...

.. image:: https://ibd-meta-analysis.herokuapp.com/assets/workflow.png
  :alt: IBD TaMMA workflow

Quick start
======================================

TaMMA is designed to be as simple, interactive and user-friendly as possible. The web app is divided into 3 different sections: 

- the top one, composed by dropdowns and by a unique legend, can be seen as the "input" section where all the general parameters are read to populate all the plots and tables
- the middle one, where all the most important plots are shown
- the bottom one, where is possible to find different tabs that will show different secondary elements like tables, infos and other plots.

Around the website, there are also some plot/table specific input elements (dropdowns, buttons, switches etc.) that are referred only the plot/table near this element. In addition, each component of TaMMA have the |info| icon that will show you a tooltip explaining the element by hovering the mouse on it.

.. |info| image:: https://ibd-meta-analysis.herokuapp.com/assets/info.png
  :alt: info  

Since TaMMA is completely interactive, any change in the input section will result in the updating of the plots all over the page with the new parameters. Some changes will trigger the update automatically (like for example changing the value of a dropdown), other will reqire the user explicit command by clicking on an "Update plot" button.

All the plots are produced using `Plotly graphing libraries <https://plotly.com/graphing-libraries/>`_, which create interactive plots where you can freely explore each graph with a series of different operations like zooming, clicking, hovering on elements etc. 
Each plot have on the top a toolbar that appear when your mouse pointer is above the graph and that allow you to get more advanced options; for exaple is possible to automatically download each plot by clicking on the camera button in this toolbar. 
Finally, even the lengend positioned under the dropdowns is interactive. You can select/unselect features of interest by simply clicking on them. By double-clicking an element you can isolate a specific feature or you can select all of them if some are unselected. 

More detailed explanation of the all the different sections and elements are listed in this documentation.

The plots
======================================

Multidimensional scaling visualization with UMAP
------------------

bla bla bla theory

In TaMMA, there are two differente UMAPs that share the same embedding: on the left a "metadata" UMAP where dots (samples) are colored by a specific user selected metadata (see :ref:`color_by_dropdown`), on the right an "expression/abundance" UMAP where dots are colored by expresion/abundance levels (see :ref:`expression_dropdown`). 
These two plots can be used to search for specific clusters od samples that share a particular metadata (on the left) or expression/abundance level (on the right) at a sample level. Samples can be filtered according to the "Color by" metadata by selecting the desired features in the legend above and then by clicking on the "Update plot" button. 
Is always possible to zoom in by clicking and dragging an area on the plot; to reset the zoom you can either double click on an empty space in the graph or click on the "Autoscale" button in the toolbar on the top of the plot. 
In the title, is possible to see how many samples are displayed (n=xxxx), the multidimensional scaling used and the metadata/gene/order/family/species used for coloring the dots. 

Since the metadata UMAP, by default, will not show its own legend (it is controlled by the general legend above), there is a switch that allow you to show the legend also on the bottom of the umap for plotting purposes. This legend will only show the selected elements in the main legend and is not interactive. 

Single feature expression/abundance visualization with Box plots
------------------

bla bla bla theory

Boxplots are useful to compare, among all the samples, the expression/abundance level of what is selected in the "Host gene / Order / Family / Species" dropdown (see :ref:`gene_species_dropdown`). By default, all the elements in the legend are shown but, by selecting specific features, is possible to show only desired boxplots. 
When the "Comparison only" switch is on, here will be present only the two condition of a selected comparison (see :ref:`contrast_dropdown`). 

.. note::

    While the selected metadata dropdown value (see :ref:`color_by_dropdown`) is "Condition", it is possible to group the boxplots by condition using the appropriate switch that is located above the graph. If the selected metadata is not "Condition", it will not be possible to use this feature.

Differential expression/abundance visualization with MA plot
------------------

bla bla bla theory

Gene ontology functional enrichment visualization with GO plot 
------------------

bla bla bla theory

The dropdowns
======================================

All the dropdowns are linekd to different plots and to other dropdowns and this means that whenever the value of a dropdown change, some specific elements in the web app will update themselfs accordingly. 

Clustering
------------------

This dropdown represent the low-dimensional embedding to use in the two UMAP plots. In this way, it is possible to see how the different samples will cluster according to the human transcriptome or, for example, to the virome or bacteriome. Changing the value in this dropdown will only update the two UMAPs, changing the position of the samples on the 2D-space of the plot.

.. _color_by_dropdown:

Color by
------------------

This dropdown will change the metadata that will be used to color the legend wich control the colors of the dots in the metadata UMAP and the boxplots. The metadata that we have collected for TaMMA are both discrete and continuous; continuous variables, like patient age, will color the dots in the UMAPs but will not plot any boxplot. 
The default value for this dropdown is "Condition" that is the union of "Tissue" and "Group" metadatas and these are used in the overall analysis to perdorm the differential gene expression. 

.. _expression_dropdown:

Expression
------------------

By changing this dropdown, you can select which expression/abundance levels you want to use for plotting the expression UMAP and the different boxplots. By selecting "Human", only the expression levels for human genes are used; by seleceting the other option you can see the abundance levels of the different meta-transcriptome components (Archaea, Bacteria, Eukaryota, Viruses) by three classification levels (orders, families and species).

.. _gene_species_dropdown:

Host gene / Order / Family / Species
------------------

This dropdown can contain different elements, depending on the expression dropdown value:

- Human: will contain around 55.000 human genes
- Archaea by... : will contain only archaeal orders/families/species, depending on the classification level choosen 
- Bacteria by... : will contain only bacterial orders/families/species
- Eukaryota by... : will contain only eukatyotic orders/families/species
- Viruses by... : will contain only viral orders/families/species

The selected element will be used to color the samples in the expression UMAP, to plot the boxplots in the different choosen metadata and can be highlighted in the MA-plot. 

Tissue
------------------

This dropdown is used to filter the following dropdown (Comparison) by a selected tissue.

.. _contrast_dropdown:

Comparison
------------------

This dropdown allow to select the comparison used for the differential gene expression and the following gene ontology enrichment analysis; thus changhing this dropdown will update both the MA-plot and the GO-plot and relative tables. The comparison follow the scheme of "Tissue Group A vs Tissue Group B". As mentioned before, the comparisons can be filtered by "Tissue". 

.. note::

    On the left of the legend, there is a "Comparison only" switch, which automatically select the two conditions in the "Comparison" dropdown (Condition1 vs Condition2); if you activate this switch while the selected metadata is not "Condition", the dropdown value will be changed too. 
    While the switch is active, changing the "Comparison" dropdown will also change the selected legend items accordingly, making very fast to focus on the specific contrast by filtering automatically metadata UMAP and boxplots. 
    If you select another condition in the legend while the switch is on and then you update the plots, the switch will be turned off. If you manually turn-off the switch, all the conditions will be automatically selected again. 

FDR
------------------

This parameter is used to control the stringency of the differential gene expression analysis and will have an effect on the number of significant differentially expressed genes (colored dots) in the MA-plot and in the DGE table (colored rows).

The tabs
======================================

Summary
------------------

bla bla bla

Metadata
------------------

bla bla bla

Box plots
------------------

bla bla bla

DGE table
------------------

bla bla bla

GO table
------------------

bla bla bla

Literature
------------------

bla bla bla

