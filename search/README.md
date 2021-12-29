### Accessing the Catalog ###

### Summary text files ###
Text files summarizing the 94 top candidates and 30 sub-threshold candidates
from the paper. The first row of the file details the column information
and data is space separated. 


#### HDF format files #####

The complete catalog with subthreshold candidates included is split between two files (due to github files size limits). The 'small' file includes 
candidates triggered with a inverse false alarm rate > .00001 years. This excludes
single-detector candidates which do not have an assigned false alarm rate. The full
file is available [from this link](https://www.atlas.aei.uni-hannover.de/work/ahnitz/4ogc/4-ogc.hdf).

```python
import h5py

catalog_high = h5py.File('./4-OGC_small.hdf', 'r')

# Selecting parts of the catalog
region = candidates['mass1'][:] + candidates['mass2'][:] < 4
lowmass_snr = candidates['H1_snr'][:][region]
```

##### File format #####
The datasets are structured arrays which have the following named columns. Some of these columns give information specific to either the 
LIGO Hanford, LIGO Livingston or Virgo detectors. Where this is the case, the name of the column is prefixed with either a `H1`, `L1`, or 'V1'.

Note: For template parameters and statistics, we report the values associated with the candidate at a given time with the lowest false alarm rate. The search
can report many candidates for a common single source due to the overlap between its many template waveforms, hence the parameters don't indicate the only template which identified a particular signal.

| Key           | Description                                                                                                                         |
|---------------|-------------------------------------------------------------------------------------------------------------------------------------|
| name          | The designation of the candidate event. This is of the form 150812_122304 ('GW is not prefixed even to confident mergers').                                                     |
| IFAR           | The rate of false alarms with a ranking statistic as large or larger than this event. The unit is yr^-1.                                                                                                           |
| stat          | The value of the ranking statistic for this candidate event.                                                                                       |
| mass1         | The component mass of one compact object in the template waveform which found this candidate. Units in detector frame solar masses. |
| mass2         | The component mass of the template waveform which found this candidate. Units in detector frame solar masses.                       |
| spin1z        | The dimensionless spin of one of the compact objects for the template waveform which found this candidate.                                                                                                                                  |
| spin2z        | The dimensionless spin of one of the compact objects for the template waveform which found this candidate.                                                                                                                                    |
| {H1/L1/V1}_end_time   | The time in GPS seconds when a fiducial point in the signal passes throught the detector. Typically this is near the time of merger.                                                                                                                              |                                                                                                                           |
| {H1/L1/V1}_snr        | The amplitude of the complex matched filter signal-to-noise observed.                                                                                                                                    |                                                      |
| {H1/L1/V1}_chisq |  Value of the signal consistency test defined in this [paper](https://arxiv.org/abs/gr-qc/0405045). This is not calculated for all candidate events. In this case a value of 0 is substituted.                                                                                                                                  |
| {H1/L1/V1}_sg_chisq      |  Value of the signal consistency test defined in this [paper](https://arxiv.org/abs/1709.08974). This is not calculated for all candidate events. In this case a value of 1 is substituted.                                                                                                                     |
| pastro |     The probability that this BBH candidate is of astrophysical origin.                                        |
               
