---
 
title: 'High Performance Computing: A library of utilities'
date: '2016-09-17T14:16:00.001-07:00'
author: Chang Liao
tags:
- HPC
- Cluster
modified_time: '2016-09-17T14:16:39.812-07:00'
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-7482752674140906664
blogger_orig_url: https://changliao.blogspot.com/2016/09/high-performance-computing-001.html
---

A brief look into all the advanced modules we can do on a typical HPC cluster. 
I will gradually introduce what I have been using over the time to advance my 
research. 

--------------------------- /opt/modules/modulefiles 
--------------------------- 
   abaqus/6.12-3 
   abinit/7.6.4_openmpi-1.8.1_intel-14.0.2.144 
   ampl/20100429 
   anaconda/2.0.1-py26 
   anaconda/2.0.1-py27                                 (D) 
   anaconda/2.0.1-py33 
   anaconda/2.0.1-py34 
   ansys/14.0 
   ansys/14.5 
   ansys/15.0 
   ansys/16.2                                          (D) 
   ansysem/16.2 
   ase/3.6.0.2515 
   ase/3.8.1.3440 
   ase/3.9.1.4567                                      (D) 
   atk/12.8.2 
   atk/13.8.0                                          (D) 
   atk/2014.1 
   atlas/3.11.30_gcc-4.7.2                             (D) 
   atlas/3.11.34_gcc-4.7.2 
   autodesk/2013 
   autodesk/2015                                       (D) 
   bbftp/3.2.0 
   bioinfo 
   boost/1.49.0 
   boost/1.53.0_intel-13.1.1.163 
   boost/1.55.0_intel-14.0.2.144 
   boost/1.57.0_intel-15.0.1.133 
   boost/1.58.0_intel-15.0.2.164 
   boost/1.58.0_intel-15.0.3.187 
   boost/1.60.0_impi-5.1.2.150_intel-16.0.1.150 
   boost/1.60.0_impi-5.1.3.181_intel-16.0.2.181 
   boost/1.60.0_intel-16.0.1.150                       (D) 
   cdat/5.2 
   cdo/1.6.9 
   cgal/4.4 
   cgal/4.6.1                                          (D) 
   clcgwb/6.5.1 
   cmake/2.8.11.2                                      (D) 
   cmake/3.1.1 
   comsol/4.4 
   comsol/5.1 
   comsol/5.1.0.145 
   comsol/5.2                                          (D) 
   cplex/12.1 
   cplex/12.6.0.0                                      (D) 
   desmond/v4.5 
   desmond/v31023 
   desmond/v38017                                      (D) 
   devel/20150609 
   dmtcp/2.0 
   doxygen/1.8.7 
   eclipse/4.2.1 
   eclipse/4.4.2                                       (D) 
   eigen/3.1.3 
   eman/1.9 
   eman/2.07                                           (D) 
   envi/4.8                                            (D) 
   envi/5.0 
   envi/5.3 
   espresso/4.0.3_impi-4.1.1.036_intel-13.1.1.163 
   espresso/4.3.2_impi-4.1.1.036_intel-13.1.1.163 
   espresso/5.1_impi-4.1.1.036_intel-13.1.1.163 
   espresso/5.2.1_impi-5.0.3.048_intel-15.0.3.187      (D) 
   ferret/6.8.4.2 
   ffmpeg/2.1.3 
   fftw/2.1.5_gcc-4.7.2_openmpi-1.8.1 
   fftw/2.1.5_intel-15.0.3.187_openmpi-1.8.1 
   fftw/3.3.4_gcc-4.7.2_openmpi-1.8.1 
   fftw/3.3.4_impi-4.1.1.036 
   fftw/3.3.4_impi-5.0.3.048 
   fftw/3.3.4_impi-5.1.1.109 
   fftw/3.3.4_impi-5.1.2.150 
   fftw/3.3.4_intel-13.1.1.163_openmpi-1.8.1           (D) 
   fftw/3.3.4_intel-14.0.2.144_openmpi-1.8.1 
   fftw/3.3.4_intel-15.0.1.133_openmpi-1.8.1 
   gamess/01.MAY.2013.R1 
   gams/24.1.1 
   gaussian03/E.01 
   gaussian09/C.01 
   gaussian09/D.01                                     (D) 
   gaussian09/E.01 
   gaussview/5.0.8 
   gcc/4.7.2                                           (D) 
   gcc/4.8.2 
   gcc/4.9.2 
   gcc/5.2.0 
   gdal/1.10.0 
   gdal/1.11.1_gcc-4.7.2                               (D) 
   gdb/7.5.1 
   geos/3.4.2_gcc-4.7.2 
   git/1.8.5.1 
   gmp/5.1.3 
   gmt/5.1.1 
   gnuplot/4.6.2 
   gpaw/0.10.0.11364_openmpi-1.8.1_intel-13.1.1.163 
   gpaw/0.11.0.13004_impi-5.1.2.150_intel-16.0.1.150   (D) 
   grads/2.0.2 
   grass/6.4.2 
   gromacs/5.0 
   gs/9.15 
   gsl/1.6 
   gsl/1.15                                            (D) 
   guile/1.8.7 
   gurobi/6.5.0 
   harminv/1.3.1 
   hdf5/1.8.7_gcc-4.7.2 
   hdf5/1.8.7_intel-13.1.1.163                         (D) 
   hdf5/1.8.7_intel-14.0.2.144 
   hdf5/1.8.7_intel-15.0.1.133 
   hdf5/1.8.12_impi-4.1.1.036 
   hdf5/1.8.12_intel-13.1.1.163 
   hdf5/1.8.13_gcc-4.7.2 
   hdf5/1.8.13_impi-5.0.3.048 
   hdf5/1.8.13_intel-15.0.1.133 
   hdf5/1.8.16_impi-5.0.3.048 
   hdf5/1.8.16_impi-5.1.2.150 
   hdf5/1.8.16_intel-15.0.3.187 
   hdf5/1.8.16_intel-16.0.1.150 
   hpc/5.3.2 
   hspice/2013.03 
   hypre/2.9.0b_impi-5.0.2.044_intel-15.0.1.133 
   hypre/2.10.0b_impi-5.0.2.044_intel-15.0.1.133 
   hypre/2.10.0b_impi-5.0.3.048_intel-15.0.2.164 
   hypre/2.11.0_impi-5.0.3.048_intel-15.0.2.164        (D) 
   idl/8.2 
   idl/8.4                                             (D) 
   imod/4.7.6 
   impi/4.1.0.030 
   impi/4.1.1.036 
   impi/5.0.0.028 
   impi/5.0.2.044 
   impi/5.0.3.048                                      (D) 
   impi/5.1.1.109 
   impi/5.1.2.150 
   impi/5.1.3.181 
   intel/12.0.084 
   intel/13.0.1.117 
   intel/13.1.1.163                                    (D) 
   intel/14.0.0.080 
   intel/14.0.2.144 
   intel/15.0.1.133 
   intel/15.0.2.164 
   intel/15.0.3.187 
   intel/16.0.0.109 
   intel/16.0.1.150 
   intel/16.0.2.181 
   jasper/1.900.1 
   java/1.6.0_45 
   java/1.7.0_21                                       (D) 
   lammps/1Feb14_intel-14.0.2.144_openmpi-1.8.1 
   lammps/15Feb16_impi-5.1.2.150 
   lammps/15May15_impi-5.0.2.044                       (D) 
   libctl/3.2.1 
   mathematica/9.0 
   matlab/R2012a 
   matlab/R2013a                                       (D) 
   matlab/R2014a 
   matlab/R2014b 
   matlab/R2015b 
   meep/1.3_impi-5.0.3.048                             (D) 
   meep/1.3_openmpi-1.8.1_gcc-4.7.2 
   molpro/2010.1.24 
   molpro/2012.1.0                                     (D) 
   mono/3.12.1 
   mopac/2012 
   mpc/0.9 
   mpfr/3.1.2 
   namd/2.9-ibverbs 
   namd/2.9-tcp                                        (D) 
   ncl/6.1.0                                           (D) 
   ncl/6.3.0 
   nco/4.4.6_intel-13.1.1.163 
   ncview/2.1.2 
   netcdf/3.6.3_gcc-4.7.2 
   netcdf/3.6.3_intel-13.1.1.163 
   netcdf/3.6.3_intel-14.0.2.144 
   netcdf/3.6.3_intel-15.0.1.133 
   netcdf/4.1.1_gcc-4.7.2_hdf5-1.8.7 
   netcdf/4.1.1_gcc-4.7.2 
   netcdf/4.1.1_intel-13.1.1.163_hdf5-1.8.7 
   netcdf/4.1.1_intel-13.1.1.163                       (D) 
   netcdf/4.1.1_intel-14.0.2.144 
   netcdf/4.1.1_intel-15.0.1.133 
   netcdf/4.3.2_intel-13.1.1.163_hdf5-1.8.12 
   netcdf/4.3.2_intel-13.1.1.163 
   netcdf/4.3.3.1_gcc-4.7.2_hdf5-1.8.13 
   netcdf/4.3.3.1_intel-15.0.1.133_hdf5-1.8.13 
   ngspice/25 
   nlopt/2.4.1 
   nwchem/6.3-src.2013-05-28 
   nwchem/6.5                                          (D) 
   octave/3.6.4 
   openfoam/2.2.0 
   openmpi/1.8.1_gcc-4.7.2 
   openmpi/1.8.1_intel-13.1.1.163                      (D) 
   openmpi/1.8.1_intel-14.0.2.144 
   openmpi/1.8.1_intel-15.0.1.133 
   openmpi/1.8.1_intel-15.0.3.187 
   openmpi/1.10.1_gcc-5.2.0 
   openmpi/1.10.1_intel-16.0.1.150 
   p4vasp/0.3.26 
   papi/4.2.0 
   parafly/r2013-01-21 
   paraview/4.2 
   pbs-spark-submit/1.5.1 
   pending 
   petsc/3.4.3_impi-4.1.0.030_intel-13.1.1.163_feast 
   petsc/3.4.3_impi-4.1.0.030_intel-13.1.1.163 
   petsc/3.4.3_impi-4.1.1.036_intel-13.1.1.163 
   petsc/3.4.4_impi-4.1.1.036_intel-14.0.2.144 
   petsc/3.5.3_impi-5.0.2.044_intel-15.0.1.133 
   petsc/3.5.3_openmpi-1.8.1_intel-15.0.1.133          (D) 
   pgi/11.8-0                                          (D) 
   pgi/12.10-0 
   pgi/13.8-0 
   pgi/14.7-0 
   pgi/14.10-0 
   pgi/15.1-0 
   pgi/15.5-0 
   pgi/15.7-0 
   pgi/15.10-0 
   pgi/16.1-0 
   pgi/16.3-0 
   pnetcdf/1.4.1_impi-4.1.1.036 
   poweracoustics/3.0b 
   powerdelta/2.1b 
   powerflow/5.0b 
   powerflow/5.1b                                      (D) 
   proj/4.8.0 
   protobuf/2.6.0 
   python/anaconda                                     (D) 
   python/2.7.2 
   python/2.7.5_intel-13.1.1.163 
   python/2.7.6_intel-14.0.2.144 
   python/2.7.8_intel-15.0.1.133 
   python/2.7.8_intel-15.0.2.164 
   python/2.7.8_intel-15.0.3.187 
   python/2.7.8_intel-16.0.0.109 
   python/2.7.8_intel-16.0.1.150 
   python/2.7.8_intel-16.0.2.181 
   python/3.4.1 
   r/2.15.1 
   r/3.1.0                                             (D) 
   r/3.2.2 
   r/3.2.3 
   rasmol/2.7.4.2 
   retools/1.3 
   root/5.34.18 
   root/5.34.30                                        (D) 
   rstudio/0.98.1056 
   sac/101.4 
   sas/9.3 
   sentaurus/2013.03 
   sietraj/349_2012-03-20 
   spark/1.5.1 
   sprng/2.0b 
   swig/2.0.4 
   tecplot/360-2013-R1                                 (D) 
   tecplot/360-2016-R2 
   thermocalc/3.1 
   tigervnc/1.2.0 
   totalview/8.11.0-0 
   totalview/8.12.0-0                                  (D) 
   totalview/8.15.0-15 
   totalview/8.15.4-6 
   use.own 
   valgrind/3.8.1 
   visit/2.6.3 
   vmd/1.9.1 
   vtk/6.0.0 
   xalt/xalt 
   xcrysden/1.5.53 
   xmgrace/5.1.22 
   xmgrace/5.1.23                                      (D) 
   xyce/6.1_tri-11.6.1_openmpi-1.8.1_intel-13.1.1.163 
   xyce/6.2_tri-11.10.2_openmpi-1.8.1_intel-15.0.1.133 
   xyce/6.2_tri-11.10.2_Serial_intel-15.0.1.133 
   xyce/6.4.0_tri11_openmpi_intel14 
   xyce/6.4.0_tri11_Serial_intel14                     (D) 

  Where: 
   (D):  Default Module 

Use "module spider" to find all possible modules. 
Use "module keyword key1 key2 ..." to search for all possible modules matching 
any of the "keys". 