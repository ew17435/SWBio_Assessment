# SWBio Data Science and Machine Learning Assessment
## Using PyMOL for the alignment and RMSD calculation of enzyme-complex structures from docking experiments

### Description
This code has been written in Python, utilising features from the python-based protein visualisation programe PyMOL, to process and compare hundreds of enzyme-complex model structures obtained from different protein docking experiments. 

Two different docking programmes (HADDOCK and BUDE) have been used to obtain structures for the complex of actACP (acyl-carrier protein) and actKR (ketoreductase) polyketide synthase enzymes which are involved in the synthesis of the polyketide antibiotic actinorhodin (act). The code is primarily written to compare the hundreds of structures resulting from several HADDOCK docking experiments with the favoured structure from previous work using BUDE, called 'M14'. Comparisons can be made after aligning the actKR protein of each HADDOCK structure with the actKR of M14. The RMSD (root-mean-square deviation - a measure of distance between backbone atoms of superimposed proteins) is then calculated to compare the similarity of the docked orientation of the actACP in HADDOCK structures with its orientation in M14. The closer the RMSD value is to 0, the more similar the orientation of actACP is between the two structures and thus the more evidence that the identified HADDOCK structure shoule be taken forward for further analysis.


### Code components

Step 1: The import of the Pymol python package

Step 2: Loading of pdb files for all protein structures from the 'Sample Data' directory

Step 3: Alignment of actKR of each HADDOCK structure to the actKR of M14

Step 4: Calculation of the RMSD of the HADDOCK actACP onto the M14 actACP


### To run:

1. Download the Python script and the Jupyter Notebook file (for reference) in this repository. Download the 'Sample Data' directory in this repository which contains all the .pdb files. Put these downloaded items into a single directory. 

2. Ensure the PyMOL python package is installed on your computer. This can be done in the Anaconda prompt by typing: ```conda install -c schrodinger pymol``` 

3. You might need to edit the .py file (and .ipynb file if using) to specify the 'target' enzyme complex which you want to compare the HADDOCK structures to. In this case it is M14, but other model complexes from previous work include M17 and M10. If different to M14 (the default written into the code), ensure you edit the script to specify the 'target' in the align_all_to_targetactKR() function and the calculate_rmsd() function. 

4. Run the .py script (I typed ```python pymol_align_rmsd_script.py``` into the JupyterLab terminal) or alternatively run each step of the code individually in the Jupyter Notebook file. When prompted add the absolute (NOT relative!) file path which leads to the directory in which the .pdb files are saved to - if you downloaded the entire 'Sample data' directory from this repository it should finish with: ```/Sample Data/```


### Output

The output in the terminal after inputting the pathname when prompted will be as below:

```PyMOL not running, entering library mode (experimental)
(loading .pdb files complete)
(alignment to M14 actKR complete)
RMSD of M14 actACP onto:
7a_1_cluster11_3 actACP = 4.773075688376693
7a_1_cluster11_1 actACP = 5.009584779342392
7a_1_cluster11_4 actACP = 5.015493295268009
6a_1_cluster3_1 actACP = 5.018795516588423
8b_2_cluster1_1 actACP = 6.324886342268573
7a_1_cluster11_2 actACP = 6.499968052288807
7a_6_cluster10_4 actACP = 6.62209567964455
8b_2_cluster1_3 actACP = 6.6468543873230335
7a_6_cluster10_2 actACP = 6.796989109232696
7a_2_cluster3_2 actACP = 6.945380366790342
7a_6_cluster10_1 actACP = 6.972798061183112
8b_9_cluster10_1 actACP = 7.2115756841947
8b_2_cluster1_2 actACP = 7.556836009686603
8b_7_cluster8_2 actACP = 7.628766120584586 
(etc.)
Analysis complete
```

Note: 

- The line ```PyMOL not running, entering library mode (experimental)``` is as a result of the PyMOL GUI not being used (it is not required for this PyMOL analysis).

- The line ```(loading .pdb files complete)``` occurs once all .pdb files are loaded. 

- The line ```(alignment to M14 actKR complete)``` occurs once all HADDOCK structure actKRs have been aligned to the M14 actKR.


The analysis is complete once a list of RMSD values corresponding to each HADDOCK structure has been produced and the terminal prints out the message: ```Analysis complete```
The resulting ordered list of HADDOCK protein structures and their corresponding RMSD values allows for the rapid identification of favourable structures to take forward for further MD simulations and hence comparable analyses between different methods of favourable conformation identification. Already, the first, second, and third highest ranked HADDOCK protein structures based on these RMSD values have been used in MD simulations.
