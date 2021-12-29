### Text file PE summary ###
The text file PETable.txt includes the summary information of the parameter estimation presented in the published paper. Additional
data is in the full hdf files which can be read as below. 

 * [PE Summary ASCII](https://github.com/gwastro/4-ogc/blob/master/posterior/PEtable.txt)

### Posterior Files in HDF format ###

To read in the posterior files, use the python environment with h5py. For example,

```
>>> import h5py
>>> fp = h5py.File('GW200219_094415-PYCBC-POSTERIOR-IMRPhenomXPHM.hdf','r')
>>> fp.keys()
<KeysViewHDF5 ['samples']>
>>> fp['samples'].keys()
<KeysViewHDF5 ['chi_eff', 'chi_p', 'dec', 'delta_tc', 'distance', 'inclination', 'loglikelihood', 'q', 'ra', 'redshift', 'spin1_a', 'spin1_azimuthal', 'spin1_polar', 'spin2_a', 'spin2_azimuthal', 'spin2_polar', 'srcmass1', 'srcmass2', 'srcmchirp']
>>> fp['samples']['chi_eff'][()]
array([ 0.09705732,  0.14272065,  0.04367346, ..., -0.10842732,
       -0.11309499, -0.15468565])
```

Provided parameters are:
 * `srcmass1`: The source-frame mass of the larger object, in solar masses.
 * `srcmass2`: The source-frame mass of the smaller object, in solar masses.
 * `srcmchirp`: The source-frame chirp mass, in solar masses.
 * `q`: The mass ratio, larger object mass to smaller object mass.
 * `chi_eff`: The effective spin of the binary.
 * `chi_p`: The precessing-spin parameter of the binary.
 * `spin1_a`: The dimensionless spin-magnitude of the larger object.
 * `spin2_a`: The dimensionless spin-magnitude of the smaller object.
 * `spin1_azimuthal`: The azimuthal angle of the spin of the larger object.
 * `spin2_azimuthal`: The azimuthal angle of the spin of the smaller object.
 * `spin1_polar`: The polar angle of the spin of the spin of the larger object.
 * `spin2_polar`: The polar angle of the spin of the spin of the smaller object.
 * `delta_tc`: The geocentric GPS time of the signal merger relative to the trigger GPS time.
 * `ra`: The right ascension of the signal (in radians).
 * `dec`: The declination of the signal (in radians).
 * `distance`: The lumionsity distance to the signal (in Mpc).
 * `redshift`: The cosmological redshift of the signal.
 * `inclination`: The inclination of the binary's orbital angular momentum with
   respect to the line of sight, in radians. An inclination of 0 (pi)
   corresponds to a face-on (face-away) orientation.
 * `loglikelihood`: The natural log of the likelihood of each sample.
