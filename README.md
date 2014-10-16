# BIOMD0000000342: Zi2011_TGFbeta_Pathway

## Installation

Download this repository, and install with distutils

`python setup.py install`

Or, install using pip

`pip install git+https://github.com/biomodels/BIOMD0000000342.git`

To install a specific version (in this example, from the 2014-09-16 BioModels release)

`pip install git+https://github.com/biomodels/BIOMD0000000342.git@20140916`

## Usage

Importing the model package.

`import BIOMD0000000342 as model`

Get the SBML string from the model

`print model.sbmlString`

If [python-libsbml](https://pypi.python.org/pypi/python-libsbml) bindings are
installed, the libsbml.SBMLDocument object is also accessible

`model.sbml`


# Model Notes


This model is from the article:  
**Quantitative analysis of transient and sustained transforming growth factor-β signaling dynamics.**   
Zhike Zi, Zipei Feng, Douglas A Chapnick, Markus Dahl, Difan Deng, Edda Klipp,
Aristidis Moustakas & Xuedong Liu _Molecular Systems Biology_ 2011 May
24;7:492. [21613981](http://www.ncbi.nlm.nih.gov/pubmed/21613981) ,  
**Abstract:**   
Mammalian cells can decode the concentration of extracellular transforming
growth factor-β (TGF-β) and transduce this cue into appropriate cell fate
decisions. How variable TGF-β ligand doses quantitatively control
intracellular signaling dynamics and how continuous ligand doses are
translated into discontinuous cellular fate decisions remain poorly
understood. Using a combined experimental and mathematical modeling approach,
we discovered that cells respond differently to continuous and pulsating TGF-β
stimulation. The TGF-β pathway elicits a transient signaling response to a
single pulse of TGF-β stimulation, whereas it is capable of integrating
repeated pulses of ligand stimulation at short time interval, resulting in
sustained phospho-Smad2 and transcriptional responses. Additionally, the TGF-β
pathway displays different sensitivities to ligand doses at different time
scales. While ligand-induced short-term Smad2 phosphorylation is graded, long-
term Smad2 phosphorylation is switch-like to a small change in TGF-β levels.
Correspondingly, the short-term Smad7 gene expression is graded, while long-
term PAI-1 gene expression is switch-like, as is the long-term growth
inhibitory response. Our results suggest that long-term switch-like signaling
responses in the TGF-β pathway might be critical for cell fate determination.

**Note:**

Developer of the model: Zhike Zi

Reference: Zi Z. et al., Quantitative Analysis of Transient and Sustained
Transforming Growth Factor-beta Signaling Dynamics, Molecular Systems Biology,
2011

1\. The global parameter that set the type of stimulation

(a) for sustained TGF-beta stimulation: set stimulation_type = 1.

(b) for single pulse of TGF-beta stimulation: set stimulation_type = 2.

parameter "single_pulse_duration" is for the duration of stimulation, for
example,

single_pulse_duration = 0.5, for 0.5 min (30 seconds) of TGF-beta stimulation.

*Note: make sure that the time course cover the time point when the event is triggered.

(c) for single pulse of TGF-beta stimulation in COPASI

change the trigger of event "single_pulse_TGF_beta_washout"

from

"and(eq(stimulation_type, 2), eq(time, single_pulse_duration))" (for SBML-SAT)

to

"and(eq(stimulation_type, 2), gt(time, single_pulse_duration))" (for COPASI)

2\. Notes for TGF-beta dose in terms of molecules per cell

(a) The following equation applies for conversion of TGF-beta dose in
molecules per cell

TGF_beta_dose_mol_per_cell = initial TGF_beta_ex*1e-9*Vmed*6e23

(b) for standard experimental setup 1e6 cells in 2 mL medium

0.001 nM initial TGF_beta_ex is approximately equal to the dose of 1200 TGF-
beta molecules/cell

0.050 nM initial TGF_beta_ex is approximately equal to the dose of 60000 TGF-
beta molecules/cell

(c) For 1e6 cells in 10 mL medium, please change the initial compartment size
of Vmed and the corresponding assignment rule for Vmed.

initial Vmed = 1e-8 (1e6 cells in 10 mL medium)

Vmed = 0.010/(1e6*exp(log(1.45)*time/1440)) (1e6 cells in 10 mL medium)

3\. Please note that this model contains events and the medium compartment
size is varied.

4\. For the model simulation in SBML-SAT, please remove initialAssignments and
save it as SBML Level 2 Verion 1 file.


