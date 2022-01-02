<h2>Performance summary</h2>
<ol>
<li>Chaput2016.csv<sup>[1]</sup></li>
<p>Benchmark: DUDE;</p>
<p>Metric: BEDROC (alpha=80.5);</p>
<p>Software: GOLD，Glide, Surflex，FlexX</p>  
<li>Cleves2020.csv<sup>[2]</sup></li>
<p>Benchmark: DUDE plus;</p>
<p>Metric: ROC AUC and ER at 1%;</p>
<p>Software: Dock, Glide, Surflex</p>
<li>Eberhardt2021.csv<sup>[3]</sup></li>
<p>Benchmark: DUDE;</p>
<p>Metric: ROC AUC,BEDROC (alpha=20),EF at 1%, 5% and 10%;</p>
<p>Software: AutoDock 1.2</p>  
</ol>
<h2>Reference</h2>
<ol>
<li>Chaput, L.; Martinez-Sanz, J.; Saettel, N.; Mouawad, L. Benchmark of Four Popular Virtual Screening Programs: Construction of the Active/Decoy Dataset Remains a Major Determinant of Measured Performance. J. Cheminform. 2016, 8 (1), 56. https://doi.org/10.1186/s13321-016-0167-x.</li>
<li>Cleves, A. E.; Jain, A. N. Structure- and Ligand-Based Virtual Screening on DUD-E + : Performance Dependence on Approximations to the Binding Pocket. J. Chem. Inf. Model. 2020, 0 (0), acs.jcim.0c00115. https://doi.org/10.1021/acs.jcim.0c00115.</li>
<p>Download: https://www.jainlab.org/downloads/</p>
<li>Eberhardt, J.; Santos-Martins, D.; Tillack, A. F.; Forli, S. AutoDock Vina 1.2.0: New Docking Methods, Expanded Force Field, and Python Bindings. J. Chem. Inf. Model. 2021, acs.jcim.1c00203. https://doi.org/10.1021/acs.jcim.1c00203.</li>
</ol>
<h2>Tools</h2>
<ol>
<li>Remove the brackets in the title tag</li>
<p>The duplicated molecules has brackets in the SDF title tag. We need to remove it before grouping molecules with aggregation funtion.</p>
<pre line="1" lang="python">
CHEMBL162 (1)
CHEMBL471526 (1)
CHEMBL452341 (1)
CHEMBL383300 (1)
CHEMBL383300 (2)
CHEMBL383300 (3)
</pre>
<p>sed command is good to do it:</p>
<pre line="1" lang="python">
>sed s/\ \([0-9]*\)//g foo.sdf >> oof.sdf
</pre>
<li>Add Title and label tags to the SDF file.</li>
<pre line="1" lang="python">
>add_label_to_sdf.py actives_final_dock.sdf actives_final_dock_label.sdf active
</pre>
<li>Group together of molecules (differnet protonation states,tautomers) with the same title stored in SDF, based on a aggregation functions such as max and min.</li>
<pre line="1" lang="python">
>extract_sdfscore2csv.py actives_final_dock_label.sdf  actives_score.csv Chemgauss4 min
</pre>
</ol>
