# Some Freesurfer useful commands

To create a CSV with cortical measures (volume, thickness, etc.) do:

```bash
aparcstats2table --subjectsfile ~/Downloads/adni_bl_subjects.csv --hemi lh --hemi rh --meas thickness --delimiter comma --tablefile ~/Downloads/meas.csv
```

For getting volumetric data:
```
asegstats2table --subjectsfile ~/Downloads/adni_bl_subjects.csv --delimiter comma --tablefile ~/Downloads/vols.csv
```

## references
  * https://surfer.nmr.mgh.harvard.edu/fswiki/aparcstats2table 
  *  https://surfer.nmr.mgh.harvard.edu/fswiki/asegstats2table 
