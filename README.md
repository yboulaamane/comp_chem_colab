# Computational chemistry on Colab

Jupyter notebooks for cheminformatics, machine learning for drug discovery and molecular
dynamics that run in [Google Colab](https://colab.research.google.com/), with nothing to
install on your computer. Each notebook installs what it needs, downloads its own data and
explains every step.

They are also hands-on companions to [Learn CADD](https://learn-cadd.vercel.app/), a course
on computer-aided drug design; the table gives the matching module for each notebook.

## Notebooks

| Notebook | What it does | Learn CADD module | Runtime |
| --- | --- | --- | --- |
| [Tanimoto similarity](Tanimoto_similarity.ipynb) <br> [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/yboulaamane/comp_chem_colab/blob/main/Tanimoto_similarity.ipynb) | Morgan fingerprints and Tanimoto similarity, for one pair and as a similarity matrix | 5. Cheminformatics & Molecular Representations | CPU |
| [Chemical space with PCA and t-SNE](t-SNE_visualizing_chemical_space.ipynb) <br> [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/yboulaamane/comp_chem_colab/blob/main/t-SNE_visualizing_chemical_space.ipynb) | Projects MAO-B actives and inactives from ChEMBL onto two dimensions | 5. Cheminformatics & Molecular Representations | CPU |
| [1D CNN on fingerprints](cnn_fingerprints_vs.ipynb) <br> [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/yboulaamane/comp_chem_colab/blob/main/cnn_fingerprints_vs.ipynb) | Classifies MAO-B actives and inactives from Morgan fingerprints, against a random forest baseline | 8. Virtual Screening Strategies <br> 9. QSAR Modeling & AI Interpretation | CPU |
| [2D CNN on structure images](cnn_images_vs.ipynb) <br> [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/yboulaamane/comp_chem_colab/blob/main/cnn_images_vs.ipynb) | The same task from 2D drawings of the structures | 8. Virtual Screening Strategies <br> 9. QSAR Modeling & AI Interpretation | GPU |
| [Molecular docking with AutoDock Vina](docking_autodock_vina.ipynb) <br> [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/yboulaamane/comp_chem_colab/blob/main/docking_autodock_vina.ipynb) | Docks inhibitors into MAO-B (PDB 2V5Z), with a redocking RMSD check and a score table | 6. Molecular Docking | CPU |
| [Protein-ligand interactions](protein_ligand_interactions.ipynb) <br> [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/yboulaamane/comp_chem_colab/blob/main/protein_ligand_interactions.ipynb) | Interaction fingerprint of the MAO-B site with ProLIF, as a table, 2D diagram and 3D view | 3. Ligand-Receptor Interactions | CPU |
| [Pharmacophore modeling](pharmacophore_modeling.ipynb) <br> [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/yboulaamane/comp_chem_colab/blob/main/pharmacophore_modeling.ipynb) | Features of a known inhibitor, then 2D and 3D pharmacophore screening with enrichment | 7. Pharmacophore Modeling | CPU |
| [Drug-likeness and ADMET](admet_druglikeness.ipynb) <br> [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/yboulaamane/comp_chem_colab/blob/main/admet_druglikeness.ipynb) | Lipinski/Veber rules, PAINS/Brenk alerts and ADMET-AI predictions | 12. In Silico ADMET & Safety | CPU |
| [Protein MD with GROMACS](MD-simulation-Gromacs.ipynb) <br> [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/yboulaamane/comp_chem_colab/blob/main/MD-simulation-Gromacs.ipynb) | Lysozyme in water, from the crystal structure to a 1 ns trajectory, its RMSD and radius of gyration | 10. MD & Free Energy Methods | GPU |

For protein-ligand MD of your own system, see [GMXFlow](https://github.com/yboulaamane/GMXFlow).

## Data

The MAO-B machine-learning notebooks (t-SNE, the two CNNs and the pharmacophore screen)
download IC50 and Ki values for human monoamine oxidase B
([CHEMBL2039](https://www.ebi.ac.uk/chembl/explore/target/CHEMBL2039)) from ChEMBL on the
first run and save the labelled compounds to `maob_chembl_labelled.csv`. ChEMBL data is
licensed under [CC BY-SA 3.0](https://creativecommons.org/licenses/by-sa/3.0/). The docking
and interaction notebooks download the MAO-B crystal structure
[2V5Z](https://www.rcsb.org/structure/2V5Z), and the GROMACS notebook downloads PDB entry
[1AKI](https://www.rcsb.org/structure/1AKI).

## Extras

[`extras/`](extras) holds general machine-learning notebooks that are not specific to
chemistry: NumPy and TensorFlow basics, dense networks on MNIST, a CNN on CIFAR-10 and the
scikit-learn example of ROC curves.

## Running locally

The notebooks also run in Jupyter on your own computer. Skip the Colab-only cells (Google
Drive, file download) and install the packages first:

```bash
pip install rdkit pandas scikit-learn imbalanced-learn seaborn tensorflow jupyter
```

The docking, interaction and ADMET notebooks need extra packages, which their first cell
installs: `meeko openbabel-wheel py3Dmol prolif admet-ai`. For the GROMACS notebook:
`conda install -c conda-forge gromacs`.

## Credits

* The PCA and t-SNE notebook is adapted from Pat Walters'
  [visualizing chemical space notebook](https://github.com/PatWalters/workshop/blob/master/predictive_models/2_visualizing_chemical_space.ipynb).
* The docking notebook uses [AutoDock Vina](https://vina.scripps.edu/) and
  [Meeko](https://github.com/forlilab/Meeko); the interaction notebook uses
  [ProLIF](https://prolif.readthedocs.io/); the ADMET notebook uses
  [ADMET-AI](https://github.com/swansonk14/admet_ai).
* The GROMACS notebook follows Justin Lemkul's
  [lysozyme in water tutorial](http://www.mdtutorials.com/gmx/lysozyme/index.html).
* The ROC notebook in `extras/` is a scikit-learn documentation example.
