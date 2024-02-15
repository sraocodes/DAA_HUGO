---
title: "CPlantBox"
description: "Here we describe the codes of CPlantBox implementation as well as the instruction to install it along with its
              inputs and outputs from developer's perspective"
layout: "model_files"
sections:
sections:
  - section_name: "Structural Module"
    description: "The structural module contains code that simulates plant growth and morphology within the CPlantBox framework. It defines the characteristics and behavior of various plant organs like roots, stems, leaves, and seeds. Additionally, it handles tropism responses, enabling plants to adjust their growth direction in response to environmental cues. In essence, this module forms the basis for realistic plant growth simulations."
    table:
      title: "Description of C++ codes in Structural Module"
      headers: ["File", "Functionality", "Variables", "I/O"]
      rows:
        - ["[Leaf.cpp](https://github.com/Plant-Root-Soil-Interactions-Modelling/CPlantBox/blob/master/src/structural/Leaf.cpp)", "Manages leaf growth and development, covering creation, parameter computation, and visualization. Includes geometric properties and connectivity.", "Leaf identification, parameters, growth factors, geometry, tropism, connectivity.", "Input: Growth parameters, environment. Output: Leaf properties."]
        - ["[MappedOrganism.cpp](https://github.com/Plant-Root-Soil-Interactions-Modelling/CPlantBox/blob/master/src/structural/MappedOrganism.cpp)", "Handles plant structural management, including 3D soil grid mapping. Oversees initialization and simulation of root and shoot systems.", "Nodes, segments, radii, organ types, soil index, plant parameters, exchange zones.", "Input: Plant structure, soil parameters. Output: Plant structure, growth data."]
        - ["[Organ.cpp](https://github.com/Plant-Root-Soil-Interactions-Modelling/CPlantBox/blob/master/src/structural/Organ.cpp)", "Serves as a base class for plant organs (seeds, roots, stems, leaves), handling their development, geometry, and tree structure.", "Nodes, segments, organ tree, parameters, type, age, status.", "Input: Development parameters, time. Output: Organ structure, growth, geometry."]
        - ["[Organism.cpp](https://github.com/Plant-Root-Soil-Interactions-Modelling/CPlantBox/blob/master/src/structural/Organism.cpp)", "Provides simulation interface and manages OrganRandomParameters. Supports RSML and handles global node and organ index counters.", "Organ parameters, node/segment geometry, indices, RNG.", "Input: Simulation parameters. Output: Organism development, geometry, RSML."]
        - ["[Plant.cpp](https://github.com/Plant-Root-Soil-Interactions-Modelling/CPlantBox/blob/master/src/structural/Plant.cpp)", "Controls plant model simulation, managing tropisms, growth functions, and post-processing. Sets up simulation callbacks for tropisms and growth.", "Tropisms, growth functions, soil lookup, parameters, state, callbacks.", "Input: Initialization, growth parameters. Output: Growth, utilities."]
        - ["[Root.cpp](https://github.com/Plant-Root-Soil-Interactions-Modelling/CPlantBox/blob/master/src/structural/Root.cpp)", "Describes root growth, managing the creation of lateral roots and root-specific parameters. Provides capabilities for time-span growth simulation.", "Root parameters, types, state, node creation, tropism.", "Input: Growth parameters, environment. Output: Root growth, new nodes/roots."]
        - ["[RootDelay.cpp](https://github.com/Plant-Root-Soil-Interactions-Modelling/CPlantBox/blob/master/src/structural/RootDelay.cpp)", "Focuses on delayed lateral root growth, inheriting from Root class. Implements delay-based lateral root emergence.", "Root delay parameters, lateral root creation, root structure.", "Input: Growth parameters with delay. Output: Delayed root growth, structure."]
        - ["[RootSystem.cpp](https://github.com/Plant-Root-Soil-Interactions-Modelling/CPlantBox/blob/master/src/structural/RootSystem.cpp)", "Manages the entire root system, including base roots and parameters. Inherits from Organism class, integrating various root dynamics.", "Root parameters, tropisms, growth functions, state, tools.", "Input: Configuration, simulation parameters. Output: Root system growth, analysis."]
        - ["[Seed.cpp](https://github.com/Plant-Root-Soil-Interactions-Modelling/CPlantBox/blob/master/src/structural/Seed.cpp)", "Defines the Seed class, representing the plant's seed and managing the development of various organs. Integrates with plant organism structure.", "Seed development, organ management, integration with plant.", "Input: Plant configuration, organ parameters. Output: Organ initialization."]
        - ["[Stem.cpp](https://github.com/Plant-Root-Soil-Interactions-Modelling/CPlantBox/blob/master/src/structural/Stem.cpp)", "Handles stem growth and development, including lateral stem emergence and parameter computation. Supports various growth scenarios.", "Growth simulation, lateral management, parameter computation, growth modes.", "Input: Parameters, growth data. Output: Stem growth, data, parameters."]
        - ["[organparameter.cpp](https://github.com/Plant-Root-Soil-Interactions-Modelling/CPlantBox/blob/master/src/structural/organparameter.cpp)", "Central to configuring organ types in plants. Manages organ-specific and randomized parameters for simulation variability.", "Organ type setup, parameter handling, random parameter management.", "Input: Organism data, configuration. Output: Organ parameters, characteristics."]
        - ["[rootparameter.cpp](https://github.com/Plant-Root-Soil-Interactions-Modelling/CPlantBox/blob/master/src/structural/rootparameter.cpp)", "Defines root-specific parameters and functionalities, handling configurations for growth dynamics and tropism.", "Root type setup, growth dynamics, tropism, distance management.", "Input: Root data, growth configuration. Output: Root parameters, characteristics."]
        - ["[seedparameter.cpp](https://github.com/Plant-Root-Soil-Interactions-Modelling/CPlantBox/blob/master/src/structural/seedparameter.cpp)", "Handles seed-specific parameters, crucial for modeling early plant development and root system initiation.", "Seed positioning, root emergence, crown configuration, tiller parameters.", "Input: Seed data, configuration. Output: Seed parameters, development."]
        - ["[stemparameter.cpp](https://github.com/Plant-Root-Soil-Interactions-Modelling/CPlantBox/blob/master/src/structural/stemparameter.cpp)", "Manages stem-specific parameters, key to modeling stem growth, branching, and structural characteristics.", "Growth dynamics, branching, tropism, lifespan, nodal functions.", "Input: Stem data, growth parameters. Output: Stem parameters, characteristics."]
        - ["[tropism.cpp](https://github.com/Plant-Root-Soil-Interactions-Modelling/CPlantBox/blob/master/src/behavioral/tropism.cpp)", "Defines tropism behaviors, implementing mechanisms like gravitropism and hydrotropism, crucial for realistic plant growth simulation.", "Various tropisms, environmental response mechanisms.", "Input: Environmental stimuli, growth parameters. Output: Growth direction, tropism responses."]

  - section_name: "Functional Module"
    description: "The Functional Module in CPlantBox includes Python and C++ scripts for plant-soil-water interactions, featuring models like the Van Genuchten model for soil water retention. It offers tools for soil parameter tables, root conductivities, and more."
    table:
      title: "Description of Python Scripts in Functional Module"
      headers: ["File", "Functionality", "Variables", "Input/Output"]
      rows:
        - ["[Photosynthesis.cpp](https://github.com/Plant-Root-Soil-Interactions-Modelling/CPlantBox/blob/master/src/functional/Photosynthesis.cpp)", "Simulates plant photosynthesis, covering water flux, carbon assimilation, and environmental interactions.", "MappedPlant object, xylem water potential, intracellular CO2, atmospheric humidity, temperature, soil matric potentials, soil conductivities, error tracking.", "Input: Environmental conditions, plant structure. Output: Water potential, gas exchange rates, photosynthetic properties."]
        - ["[Perirhizal.cpp](https://github.com/Plant-Root-Soil-Interactions-Modelling/CPlantBox/blob/master/src/functional/Perirhizal.cpp)", "Calculates root segment radii based on volume, surface, or length.", "Volume type, cell volumes, segment lengths, cell/segment IDs, radii.", "Input: Volume type, cell volumes. Output: Outer radii for root segments."]
        - ["[CellVariablemod.py](https://github.com/Plant-Root-Soil-Interactions-Modelling/CPlantBox/blob/master/src/functional/CellVariablemod.py)", "Extends FiPy library for plant physiological simulations, handling water and nutrient transport.", "Custom CellVariablemod, FaceVariablemod, _AddOverFacesVariablemod, _FaceGradVariablemod, _ArithmeticCellToFaceVariablemod, mesh attributes, orientations, area/volume calculations.", "Input: Plant tissue structure. Output: Transport and flow properties in plant tissues."]
        - ["[ExudationModel.h](https://github.com/Plant-Root-Soil-Interactions-Modelling/CPlantBox/blob/master/src/functional/ExudationModel.h)", "Models root exudation, considering root growth dynamics and soil properties.", "Q, Dl, theta, R, k, l, grid, type, n0, thresh13, calc13, observationRadius, root system data.", "Input: Root system, simulation time, parameters. Output: Exudate distribution in soil."]
        - ["[HydraulicsDoussan.py](https://github.com/Plant-Root-Soil-Interactions-Modelling/CPlantBox/blob/master/src/functional/HydraulicsDoussan.py)", "Implements Doussan's root hydraulic model for water movement in roots.", "Root system (rs), soil matrices, kr_f, kx_f, simulation time, root xylem potentials (rx), axial and transpirational flux.", "Input: Root structure, environment. Output: Conductivity, axial fluxes, xylem potentials."]
        - ["[Leuning.py](https://github.com/Plant-Root-Soil-Interactions-Modelling/CPlantBox/blob/master/src/functional/Leuning.py)", "Implements the Leuning model for water movement and photosynthesis in plants.", "Qlight, VPD, Tl, soil matric potentials, xylem conductivities, root xylem potentials, CO2 concentration, stomatal conductance.", "Input: Plant data, environment. Output: Xylem potentials, stomatal conductance, assimilation rates."]
        - ["[van_genuchten.py](https://github.com/Plant-Root-Soil-Interactions-Modelling/CPlantBox/blob/master/src/functional/van_genuchten.py)", "Implements the Mualem - van Genuchten model for soil water.", "Pressure head, hydraulic conductivity methods, theta_R, theta_S, alpha, n, Ksat.", "Input: Soil water content, parameters. Output: Pressure head, water content, saturation, conductivity."]
        - ["[root_conductivities.py](https://github.com/Plant-Root-Soil-Interactions-Modelling/CPlantBox/blob/master/src/functional/root_conductivities.py)", "Provides functions for root conductivities in growth simulations.", "Initialization of constant and age-dependent conductivity values.", "Used in root hydraulic properties setup."]
        - ["[phloem_flux.py](https://github.com/Plant-Root-Soil-Interactions-Modelling/CPlantBox/blob/master/src/functional/phloem_flux.py)", "Simulates phloem flux and related processes.", "Segment ages, node indices, organ types, hydraulic properties.", "Input: Root system data, model parameters. Output: Phloem flux results."]
        - ["[Mesh1Dmod.py](https://github.com/Plant-Root-Soil-Interactions-Modelling/CPlantBox/blob/master/src/functional/Mesh1Dmod.py)", "Enhances FiPy's Mesh1D for 3D root system modeling in plants.", "Radii, length, vertex coordinates, face normals, methods for cell volumes, face areas, geometric aspects.", "Input: Root system data. Output: Adapted mesh properties."]
        - ["[Perirhizal.py](https://github.com/Plant-Root-Soil-Interactions-Modelling/CPlantBox/blob/master/src/functional/Perirhizal.py)", "Analyzes perirhizal zones in root systems.", "Soil volume cells, bounding box dimensions, zone densities, segment parameters, outer radii calculations, 3D Voronoi diagrams.", "Input: Root segment data. Output: Perirhizal zone analysis."]
        - ["[XylemFlux.cpp](https://github.com/Plant-Root-Soil-Interactions-Modelling/CPlantBox/blob/master/src/functional/XylemFlux.cpp)", "C++ module for xylem and soil flux simulation.", "Linear system assembly, segment/soil flux computation, conductivity settings.", "Used in water flow simulation within plant xylem."]
        - ["[bresenham3D.py](https://github.com/Plant-Root-Soil-Interactions-Modelling/CPlantBox/blob/master/src/functional/bresenham3D.py)", "Implements 3D Bresenham's algorithm for line generation.", "Line drawing function, sphere function for 3D structures.", "Input: Line coordinates. Output: 3D line points."]
        - ["[xylem_flux.py](https://github.com/Plant-Root-Soil-Interactions-Modelling/CPlantBox/blob/master/src/functional/xylem_flux.py)", "Models water movement in plant xylems.", "Root system, hydraulic properties, node/segment info, flux values, soil characteristics, computational matrices.", "Input: RSML root structure files. Output: Xylem pressures, flux values."]
        - ["[StomataModel.py](https://github.com/Plant-Root-Soil-Interactions-Modelling/CPlantBox/blob/master/src/functional/StomataModel.py)", "Hybrid solver for stomatal conductance and xylem water movement.", "PAR, VPD, temperatures, soil matric potentials, root xylem pressure.", "Input: Root data, environmental factors. Output: Stomatal conductance, xylem pressure."]


---