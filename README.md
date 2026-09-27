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
| [Protein MD with GROMACS](MD-simulation-Gromacs.ipynb) <br> [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/yboulaamane/comp_chem_colab/blob/main/MD-simulation-Gromacs.ipynb) | Lysozyme in water, from the crystal structure to a 1 ns trajectory, its RMSD and radius of gyration | 10. MD & Free Energy Methods | GPU |

For protein-ligand MD of your own system, see [GMXFlow](https://github.com/yboulaamane/GMXPlotter).

## Data

The three MAO-B notebooks download IC50 and Ki values for human monoamine oxidase B
([CHEMBL2039](https://www.ebi.ac.uk/chembl/explore/target/CHEMBL2039)) from ChEMBL on the
first run and save the labelled compounds to `maob_chembl_labelled.csv`. ChEMBL data is
licensed under [CC BY-SA 3.0](https://creativecommons.org/licenses/by-sa/3.0/). The GROMACS
notebook downloads PDB entry [1AKI](https://www.rcsb.org/structure/1AKI).

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

For the GROMACS notebook: `conda install -c conda-forge gromacs`.

## Credits

* The PCA and t-SNE notebook is adapted from Pat Walters'
  [visualizing chemical space notebook](https://github.com/PatWalters/workshop/blob/master/predictive_models/2_visualizing_chemical_space.ipynb).
* The GROMACS notebook follows Justin Lemkul's
  [lysozyme in water tutorial](http://www.mdtutorials.com/gmx/lysozyme/index.html).
* The ROC notebook in `extras/` is a scikit-learn documentation example.
