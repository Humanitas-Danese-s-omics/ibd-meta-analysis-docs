.. TaMMA documentation master file, created by
   sphinx-quickstart on Fri Apr 23 15:27:36 2021.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

.. image:: https://github.com/Humanitas-Danese-s-omics/ibd-meta-analysis-docs/images/logo.png
  :alt: IBD TaMMA logo

.. toctree::
   :maxdepth: 2
   :caption: Contents:

Welcome to IBD TaMMA's documentation
======================================

What's the goal ...

.. image:: https://github.com/Humanitas-Danese-s-omics/ibd-meta-analysis-docs/images/workflow.png
  :alt: IBD TaMMA workflow

Quick start
======================================

TaMMA is designed to be as simple, interactive and user-friendly as possible. The web app is divided into 3 different sections: 

- the top one, composed by dropdowns and by a unique legend, can be seen as the "input" section where all the general parameters are read to populate all the plots and tables
- the middle one, where all the most important plots are shown
- the bottom one, where is possible to find different tabs that will show different secondary elements like tables, infos and other plots.

Around the website, there are also some plot/table specific input elements (dropdowns, buttons, switches etc.) that are referred only the plot/table near this element. In addition, each component of TaMMA have the |info| icon that will show you a tooltip explaining the element by hovering the mouse on it.

.. |info| image:: https://github.com/Humanitas-Danese-s-omics/ibd-meta-analysis-docs/images/info.png
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

Multidimensional scaling by Uniform Manifold Approximation and Projection (UMAP) consists of the low-dimensional (UMAP1 and UMAP2) embedding of high-dimensional data (e.g., 55k genes in the human transcriptome) and is, therefore, a powerful visualization to get similarities and differences between the samples.

In TaMMA, there are two differente UMAPs that share the same embedding: on the left a "metadata" UMAP where dots (samples) are colored by a specific user selected metadata (see :ref:`color_by_dropdown`), on the right an "expression/abundance" UMAP where dots are colored by expresion/abundance levels (see :ref:`expression_dropdown`). 
These two plots can be used to search for specific clusters od samples that share a particular metadata (on the left) or expression/abundance level (on the right) at a sample level. Samples can be filtered according to the "Color by" metadata by selecting the desired features in the legend above and then by clicking on the "Update plot" button. 
Is always possible to zoom in by clicking and dragging an area on the plot; to reset the zoom you can either double click on an empty space in the graph or click on the "Autoscale" button in the toolbar on the top of the plot. 
In the title, is possible to see how many samples are displayed (n=xxxx), the multidimensional scaling used and the metadata/gene/order/family/species used for coloring the dots. 

Since the metadata UMAP, by default, will not show its own legend (it is controlled by the general legend above), there is a switch that allow you to show the legend also on the bottom of the umap for plotting purposes. This legend will only show the selected elements in the main legend and is not interactive. 

.. _boxplots:

Single feature expression/abundance visualization with Box plots
------------------

Box plots are useful to compare, among all the samples, the expression/abundance level of what is selected in the "Host gene / Order / Family / Species" dropdown (see :ref:`gene_species_dropdown`). By default, all the elements in the legend are shown but, by selecting specific features, is possible to show only desired boxplots. 
When the "Comparison only" switch is on, here will be present only the two condition of a selected comparison (see :ref:`contrast_dropdown`). 

.. note::

    While the selected metadata dropdown value (see :ref:`color_by_dropdown`) is "Condition", it is possible to group the box plots by condition using the appropriate switch that is located above the graph. If the selected metadata is not "Condition", it will not be possible to use this feature.

.. _ma_plot:

Differential expression/abundance visualization with MA plot
------------------

MA plots are very useful for the visual representation of differential analyses of omics-derived data. They show sample dispersion in accordance with average expression (A) and the log2 fold change between the two conditions of interest (M).

This plot shows either the differential gene expression (in case the Expression dropdown is set to "Human", see :ref:`expression_dropdown`) or the differential order/family/species abundance (in case the Expression dropdown is set to any non-human value).

In case of a human expression dataset, is possible to explore the differential gene expression for a specific comparison for all the different genes. In the plot, the upregulated and downregulated genes relative to the comparison, given a specific stringency (see :ref:`stringecy_dropdown`), are colored in red (up) and in blue (down). On the right, is possible to highlight the gene selected by also showing its related data and statistics by clicking on the button "Show gene statistics". 
In any other case, instead of genes are plotted orders, families or species relative to the different kingdom choosen in the dropdown but all the underlying logic is the same as a human expression dataset. 

If you are interesetd in a particolar element, is possible to click on its dot to automatically select it in the Host gene / Order / Family / Species dropdown (see :ref:`gene_species_dropdown`), updating all the related graphs accordingly.

.. _go_plot:

Gene ontology functional enrichment visualization with GO plot 
------------------

Functional enrichment analysis uses statistical approaches to highlight under- or over-represented groups of genes or proteins that belong to specific biological processes.

Through this plot is possible to explore the gene ontology for the human transcriptome and the selected comparison (see :ref:`contrast_dropdown`). By default are shown the top 15 significant (P-value is represented by color intensity) up (red dots) and down (blue dots) GO categories, ordered by enrichment (dot dimension), for the selected comparison. Is possible to search for specific keyword to filter the gene ontology dataset thanks to a search bar located on top of the plot. You can tipe here any keyword that will be search in the description of each GO category; in alternative you can directly type a GO ID (for example, GO:0090263). This filtering will also filter the GO table in the same way (see :ref:`go_table`).

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

.. _stringecy_dropdown:

FDR
------------------

This parameter is used to control the stringency of the differential gene expression analysis and will have an effect on the number of significant differentially expressed genes (colored dots) in the MA-plot and in the DGE table (colored rows).

The tabs
======================================

In the bottom part of the web app, there are a number of tabs with other secondary content, spacing from plots, links, images to exportable tables. 

Summary
------------------

In this tab there are general information about TaMMA as well as reference links and project info. 
The only graph here is a Snakey to represent the relationships in number of samples shared between two selected metadata. By hovering the mouse on the link, is possible to see the number of shared samples, for example the "CD" metadata and the "Ileum" metadata are present in around 1380 samples. 

Metadata
------------------

In this tab, there is the full metadata table used to populate the :ref:`color_by_dropdown` plus other info like, for example, the GSE link to the specic study on `NCBI GEO <https://www.ncbi.nlm.nih.gov/geo/>`_. The table have natve sorting and filtering (by exact match) interactivity options. 

.. _multiboxplots_tab:

Box plots
------------------

In this tab, you can easily plot many series of boxplots of different items depending on the :ref:`expression_dropdown`, human genes if is selected "Human" or orders/families/species if another value is selected. For performance and usability reasons, is possible to plot at most 10 elements at time.
To select the elements to plot, you have tow different options:

- search and manually select into the dropdown one element at time
- search many elements in one click by using the text area below the dropdown. 

The search area is flexible; for genes it is case unsensitive and you can provide genes separated by whitespaces, commas, or semicolon; for other elements is still case unsensitive but you need to put one item per line. If one or more element are not found in using the text area, a message will appear below it, indicating for which element any match has been found. In these cases we invite you to check for spelling errors, typos or to directly search in the dropdown. 

.. note::

    Like for :ref:`boxplots`, while the selected metadata dropdown value (see :ref:`color_by_dropdown`) is "Condition", it is possible to group, the box plots by condition using the appropriate switch that is located below the search button. If the selected metadata is not "Condition", it will not be possible to use this feature.

.. _dge_table:

DGE table
------------------

In this tab you can explore the differential gene expression or the order/family/species abundance (depending on the :ref:`expression_dropdown` dropdown) table. Significant elements (see :ref:`stringecy_dropdown` for stringecy details) rows are colored: red for upregulated genes or overepresented orders/families/species, blue for downregulated genes or uderrepresented orders/families/species respect to the comparison selected (see :ref:`contrast_dropdown`). The table natively support sorting of columns values.

For each row in the table, there is a number of links to external resources:

- `NCBI Gene <https://www.ncbi.nlm.nih.gov/gene/>`_ or `NCBI Genome <https://www.ncbi.nlm.nih.gov/genome/>` depending on the expression dropdown
- `Ensembl <https://www.ensembl.org/index.html>`_ (only for "Human" expression dropdown)
- `GeneCards <https://www.genecards.org/>`_ (only for "Human" expression dropdown)
- `IBD exome browser <https://ibd.broadinstitute.org/>`_ (only for "Human" expression dropdown)
- `GWAS Catalog <https://www.ebi.ac.uk/gwas/>`_ (only for "Human" expression dropdown which have both "Gene" and "Gene ID" columns filled)
- `GTEx portal <https://www.gtexportal.org/home/>`_ (only for "Human" expression dropdown which have both "Gene" and "Gene ID" columns filled)

Since the table will have many entries (for Human transcriptome there will be more than 55.000 rows), you can filter this table by selecting mutiple elements in the dropdown, creating a filtered version of the table on top of the full table. 

It is possible to easily download both the full and filtered tables by clicking on the respectiv download buttons. 

.. note::

    Similar to :ref:`ma_plot`, clicking on a Gene/Order/Family/Species cell will change the selected element in the right dropdown (see :ref:`gene_species_dropdown`), thus updating all the relevant plots. 

.. _go_table:

GO table
------------------

Here is showed the table for the gene ontology analysis obtained, for the selected comparison (see :ref:`contrast_dropdown`), with an FDR < 1e-10. As for genes in the :ref:`dge_table`, significant GO categories rows for the GO analysis (P-value < 0.05) are colored in red if upregulated or in blue if downregulated. The table natively support sorting of columns values. Each GO ID is a link of the correspective GO category in the `AmiGO <http://amigo.geneontology.org/amigo>`_ website. 

As explained in :ref:`go_table`, this table can be filtered using the GO plot keyword search bar: the GO categories plotted will be the one that will be present in the table. Like the DGE table, you can easily download both the full or the filtered table using the download buttons. 

.. note:

    You can select and copy the content of the "Genes" column (using ctrl/cmd + c on your keyboard) and paste it on the search area of the :ref:`multiboxplots_tab` tab to plot genes relevant for a particular GO category of your choice. Remember to select "Human" in the :ref:`expression_dropdown` dropdown and remember limit of 10 genes for plot.

Literature
------------------

Here we collected a series of evidence collected by using TaMMA referred to many different scientific publications and topics. The plots here are not related to any of the dropdowns on the top of the website and are not interactive. 
