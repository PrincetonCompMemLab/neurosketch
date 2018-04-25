# Goal of study 
How are visual production and visual recognition of objects related in the brain?
How does visual production training influence organization of neural object representations?

# Experimental procedure

10 runs in total: 2 (localizer recognition runs) + 2 (pre recognition runs) + 4 (drawing runs) + 2 (post recognition runs)

4 objects: bed, bench chair, table.
Viewed each object 20 times per run during recognition runs. Trial ISI jittered. 
Two objects drawn in alternating sequence during drawing runs. Each drawing trial lasted 23 TR’s.

# Scanning parameters & sequence information

TODO

# fMRI data preprocessing

## INPUT:  
.nii.gz, .bxh files, and trial metadata stored on mongo (currently hosted on kanefsky)

Motion correction
Projection of filtered_func into anatomical space to yield 4D timeseries
ROIs:
Freesurfer used to derive ROIs from each participants’ T1
Univariate comparison (drawing vs. not drawing) used to make task mask
ROIs with ‘draw’ suffix are intersects of ROI masks and draw task mask
All in anatomical space

## OUTPUT: 
	For each ROI and each subject:
voxel matrices (m timepoints x n voxels) saved as .npy
metadata saved as .csv
Note: before 4/23/18, canonical voxel matrices + metadata were in `neurosketch/data/neurosketch_voxelmat3mm_freesurfer_drawing`, renamed to `neurosketch/data/features/drawing`. 

	Note: path on jukebox (accessible via Spock) is: `PATH/PATH/PATH`




# Main analyses 

## INPUT to analysis:

There is a master DATA dir containing all processed fMRI data in standard format:
* `DATA/features` contains all feature matrices and metadata from all phases, ROIs, and subjects.
	* `DATA/features/drawing` contains drawing filtered func data (represented as .npy feature matrices) + corresponding metadata 
	* `DATA/features/recog` contains recognition filtered func data (represented as .npy feature matrices) + corresponding metadata
* `DATA/copes` contains all cope NIFTI files from GLM fit to recognition and drawing runs for all subjects.
	* `DATA/copes/recog/objectGLM` recognition cope maps from object GLM
	* `DATA/copes/draw/taskGLM` drawing cope maps from drawing_task GLM

# List of main analysis notebooks:
* Pre-Post Representational Similarity Analyses on Recognition Data
- How correlated are individual differences in prepost differentiation across different ROIs? (matrix plot)

* Measure Evidence for Objects During Drawing
	- Using neural patterns from localizer recognition runs
	- How correlated are logistic classifier predictions across different ROIs? (matrix plot)	
	- Using VGG features

* Relate Drawing and Differentiation

* Measure Informational Connectivity within Drawing Regions


