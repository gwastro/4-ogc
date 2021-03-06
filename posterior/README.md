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
<KeysViewHDF5 ['chi_eff', 'chi_p', 'coa_phase', 'comoving_volume', 'dec', 'delta_tc', 'distance', 'inclination', 'loglikelihood', 'q', 'ra', 'redshift', 'spin1_a', 'spin1_azimuthal', 'spin1_polar', 'spin2_a', 'spin2_azimuthal', 'spin2_polar', 'srcmass1', 'srcmass2', 'srcmchirp']>
>>> fp['samples']['chi_eff'][()]
array([-0.15618938, -0.21925095,  0.03480148, ...,  0.14123062,
       -0.04531827, -0.1313231 ])
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
 * `lambda1`: The tidal deformability of the primary component (applicable to the binary neutron star events).
 * `lambda2`: The tidal deformability of the secondary component (applicable to the binary neutron star and the neutron star-black hole events).
 * `delta_tc`: The geocentric GPS time of the signal merger relative to the trigger GPS time.
 * `ra`: The right ascension of the signal (in radians).
 * `dec`: The declination of the signal (in radians).
 * `distance`: The luminosity distance to the signal (in Mpc).
 * `comoving_volume`: The comoving volume correspoinding to the luminosity distance of the signal (in Mpc^3).
 * `redshift`: The cosmological redshift of the signal.
 * `inclination`: The inclination of the binary's orbital angular momentum with
   respect to the line of sight, in radians. An inclination of 0 (pi)
   corresponds to a face-on (face-away) orientation.
 * `loglikelihood`: The natural log of the likelihood of each sample.
 * `coa_phase`: The coalescence phase of the signal merger. There is no coa_phase for the binary neutron star events because it has been analytically marginalized over.
