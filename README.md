UK_biobank_pipeline
===================

The `UK_biobank_pipeline` project is a multi-modal MRI processing pipeline written in Python, bash, MATLAB, and R. It uses [FSL](http://fsl.fmrib.ox.ac.uk/fsl/fslwiki/) as the basic building blocks.

The McIntosh Lab implementation includes the addition of a user-provided parcellation for 1) computing ROI-based timeseries and functional connectivity (Pearson correlations) using resting-state fMRI; and 2) connectome construction using diffusion-weighted imaging tractography.



Dependencies
------------

The only external dependencies required for this pipeline are:
* FSL
* AFNI
* Freesurfer
* Anaconda/Miniconda
* git (>=2)


Installation
------------

1) Download the release .zip from the repository.
2) Unzip the .zip file to where you'd like the pipeline to be installed; e.g. unzipping it in `/home/username` will yield `/home/username/ukbb`
3) `cd` into ukbb and run `chmod +x install_ukbb.sh`
4) Run `./install_ukbb.sh`
5) Once the installer finishes, `cd` into `ukbb-mclab` and edit file `init_vars`. Lines specified with `#TO BE MODIFIED BY USER` are the only lines you should need to change.

Note: at present, changes may need to be made to the code handling SGE queuing depending on your system. Currently we use queues `all.q` and `bigmem_16.q`; adding queues with those names will drastically reduce queue configuration.


Documentation
-------------

The original `UK_biobank_pipeline` is explained in detail in the paper [Image Processing and Quality Control for the first 10,000 Brain Imaging Datasets from UK Biobank](http://www.biorxiv.org/content/early/2017/04/24/130385).

Tractography for connectome construction is based on methods validated using tracer data in macaques (see Shen et al. 2019 https://doi.org/10.1016/j.neuroimage.2019.02.018).


***Notes***
-----------

At present, this pipeline cannibalizes subject directories. It is strongly advised to make a copy of subject directories and to run the pipeline on those copies until we correct that behaviour.

Parameter settings for processing toolboxes need to be customized to the acquisitions. It is advised that you review parameter choices for FSL tools including, but not limited to, EDDY, BEDPOSTX, PROBTRACKX2, FEAT, and FIX.

Currently, gradient distortion correction, TOPUP distortion correction, NODDI,  AUTOPTX and susceptibility-weighted imaging processing from the original UKBiobank pipeline are either not implemented or remain untested.