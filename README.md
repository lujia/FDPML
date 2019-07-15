# Frequency Domain Perfectly Matched Layer (FDPML)

## Introduction

FDPML is a computational method to simulate heat transport through nanostructured materials. The method converts atomistic equations of motion for every atom inside a simulation domain to a set of linear algebraic equations. The equations can then be solved using iterative solvers. The model is efficient as it stores the matrices in sparse format (COO), while also being able to be deployed across multiple cluster node.

For a more detailed mathematical discription of the mode please refer  
`kakodkar et. al. Journal of Applied Physics 118, 094301 (2015)`

## Installation

### Dependencies

1. MPI
1. openmpi FORTRAN90 Compiler
1. IntelMKL

Clone this repository using `git clone git@github.com:Rohit-Kakodkar/FDPML.git`

Install using Makefile : `make all`

Upon installation execultables will be created in `\bin` folder

## Usage

The method can be used to obtain 2 properties intrinsic to heat transport through nanostructured materials.

1. Transmission coefficient across interfaces- Please refer [here](https://journals.aps.org/prb/abstract/10.1103/PhysRevB.95.125434)
2. Scattering Cross-section due to nanoparticles- Please refer [here](https://aip.scitation.org/doi/abs/10.1063/1.5031757)

Input parameters for simulations are specified through input cards described below

All quantities whose dimensions are not explicitly specified are in RYDBERG ATOMIC UNITS. Charge is "number" charge (i.e. not multiplied by e); potentials are in energy units (i.e. they are multiplied by e).

Structure of the input data:

	`&filenames
		...
	/
	`






<!-- # Frequency Domain Perfectly Matched Layer

For technical details on the method please refer :

kakodkar et. al. Journal of Applied Physics 118, 094301 (2015)

========================================================================================

Pre-requisites:	Primary domain should be generated using gendomain.f90 provided in this repository

Force constant file should generated using Quantum Espresso in *.fc format


 	FDPML calculates scattering properties for a particular phonon mode
	(wavevector and polarization resolved) inside nanostructured materials.
	For in-depth discription of the method refer
	kakodkar et. al. Journal of Applied Physics 118, 094301 (2015)

	Input cards :

	&filenames
		flfrc1 = force constant file of the matrix material (should be generated via
				 Quantum espresso). NOT IN XML FORMAT
		flfrc2 = force constant file of impurity material (should be generated via
				 Quantum espresso). NOT IN XML FORMAT
		mass_input = logical, if true masses are calculated with atomic resolution
							  else masses are calculated based on supercell
		mass_file = mass domain file generated by gendomain.f90
		domain_file = domain specification generated by gendomain.f90

	&system
		simulation_type = 'interface' or 'nanoparticle'
		PD = size of the primary domain, should be same as the one generated
			 gendomain.f90
		LPML = length of PML. Ignored if PML calculation is auto
		periodic = logical, if true applied periodic boundaries in x and y direction
		crystal_coordinates = logical, if true work in crystal coordinates
		asr = acoustic sum rule. Refer QE documentation
		wavetype = 'half' or 'full' to specify type of incidnet wave
		q = wavevector, ignored if mp = .true.
		mode = polarization
		sigmamax = maximum value of damping coefficient, Ignored if PML calculation is auto
		mp = generate qpoint list base Monkhorst Pack(MP) grid
		qpoint = n, then choose nth q from list of q generated by MP grid
		nk1, nk2, nk3 = k-spacings in x,y and z directions for MP grid

	&postprocessing
		calc_TC = logical, calculate transmission coefficient (for interface problems)
		calc_gam = logical, calculate scattering cross-section (for nanoparticle problems)

	&plotting
		plot_K  = logical, plot variation of K vector on TD(3)/2 plane
		plot_uinc = logical, plot incident wave
		plot_uscat = logical, plot scattered wave
		plot_sig = logical, plot variation of damping coefficient
		plottingmode = 1, 2, or 3, plot x, y, or z components of above properties -->
