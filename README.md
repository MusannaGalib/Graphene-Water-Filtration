**Computational dataset for research paper** [**Molecular Dynamics Simulation and Experimental Fabrication of Nanoporous Graphene Membranes for Optimal Water Permeability in Reverse Osmosis Desalination**](http://api.apoorvk.me/files/NPG-Desalination/ResearchPaper.pdf) **by Apoorv Khandelwal**

**Molecular Dynamics Simulation Scripts for use with** [**LAMMPS software**](http://lammps.sandia.gov/)

**&quot;Input Script Generation.sh&quot;** (bash file)

-  Generates LAMMPS input file for variations in trials
-  Constant temperature &amp; pressure; up to 5 pores and 3 seed values per pore count

**&quot;Calculations&quot;** : Membrane porosity and pressure calculations

**&quot;Results&quot;** : Molecular filtration and system states over time for varied porosity trials

**&quot;Dataset&quot;** : Input scripts &amp; sample data

- Files contained here can be run with LAMMPS to produce sample trial
- Contents:
  - **&quot;Batch Jobs.sh&quot;**: run all trials on supercomputer (where each trial has an execution script)
  - **&quot;scripts&quot; folder**: contains each trial&#39;s batch file to run on supercomputer
  - **&quot;pore1.seed1 (sample data)&quot; folder**
    - **&quot;RESTART&quot; folder:** recovery files in case of runtime crash
    - **&quot;Trajectories&quot;** folder: contains output of atomic positions (can be rendered with OVITO software)
    - **&quot;CH.airebo\_real&quot;**: parameter file for AIREBO potential in _real_ units
    - **&quot;graphene.hydrogen.pore1.dat&quot;**: molecular geometry for system (can be opened in Avogadro or VMD)
    - **&quot;hydrogen.pore1.seed1.in&quot;**: input script generated for trial
    - **&quot;lammps.pore1.seed1.log&quot;**: full runtime log

**LAMMPS Input Files:**

-  Establish system parameters and input from molecular geometry
-  Set interaction parameters &amp; Lennard-Jones/Coulumbic
-  Regions &amp; groups (water, membrane, pistons)
- **Minimization:** fix and relax bodies (set zero force on pistons)
- **Equilibration:** Set 150 MPa pressure on both pistons for 40-60 picoseconds (seed dependent)
- **Dynamics:** 10 nanosecond simulation of 32 MPa transmembrane pressure
- **Output:** Water molecule count on both sides of membrane, pressure, temperature, salt ion count
  -  Full atomic trajectory dump per 500 fs
  -  Restart file dump per 1.25 ns

**Supercomputer details:**

-  [San Diego Supercomputer Center Comet](https://www.sdsc.edu/support/user_guides/comet.html)
  -  LAMMPS module preinstalled
  -  24 cores/node &amp; used 4 nodes per trial (45 hr. ea.)
- **Login:** ssh user@comet.sdsc.edu
-  Trials were run in the &quot;pore1.seed1&quot; folder with Linux command:<br>**lammps -in hydrogen.pore1.seed1.in -log lammps.pore1.seed1.log**
