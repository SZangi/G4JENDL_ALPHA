This repo is intended to provide users with data files for use with Geant4 simulations, processed from the JENDL5 alpha sublibrary. The intended purpose of these files was initially to simulate (alpha,n) reactions in Carbon, and thus, the processing has been performed in such a way that the (alpha,n) reaction cross section will be correct when these files are used with the G4ParticleHP models. They have not been verified to correctly reproduce other reaction cross sections, and thus users should be wary of their accuracy for other use cases. 

The processing of the files was done with the code provided in the ENDF_2_G4 folder, and follows broadly the steps outlined below:

1. The files are checked to make sure they are properly ENDF formatted
2. The files are converted to be linear-linear interperoable
3. The data in the relevant MT_MF number is read into a python file and either:  
  a) Read directly into the Geant4 data format if the total inelastic cross-section is provided  
  b) The neutron production cross-section and non-neutron producing inelastic cross-section are summed and then read into the Geant4 data format, or  
  c) The ratio of neutorn producing cross-section to total cross-section is pulled from the TENDL-19 file for the reaction, and used to convert neutron production to total cross section which is then read into the Geant4 format

4. The human readable text file is then compressed to the .z format used by the Geant4 libraries

So far the following files have been processed:
- 13C
- 9Be
