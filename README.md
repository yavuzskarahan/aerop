for TUBITAK (The Scientific and Technological Research Council of Turkiye) 2204-A: 
## Deep Reinforcement Learning approach to Environment-depented Aerodynamic Propeller Design Optimization Problem

The project includes 4 basic components:
- Procedural Airfoil Generator
- Procedural Propeller Generator
- Automated CFD Simulator
- PPO Model

### General Information
|   |   |
|---|---|
|**Algorithm**              |   PPO (stable_baselines3) |
|**Aerodynamic Solver**     |   OpenFOAM|
|**Observation**				  | Environment parameters and propeller parameters|
|**observation_space_size** |   7a + 6 (a = airfoil number, There are 7 parameters for each arifoil and 3 propeller properties and 3 enveroiment parameters.)|
|**Action**			    | Change in all propeller parameters|
|**action_space_size**	  |   7a + 3 (a = airfoil number, There are 7 parameters for each arifoil and 3 enveroiment parameters.)|
|**Reward**                 |   Change in Aerodynamic Effiency ($\Delta \eta$)|

_____________________________________________________________
### Environment Properties
| parameter_name     | observation_space  |
|---|---|
| $\text{Re} (\frac{\rho v l}{\mu})$[^1]       | ?                  |
| $\text{rpm}$      | ?                  |

### Propeller Properties
| parameter_name     | observation_space  | action_space  |
|---|---|---|
| bladeNumber (int)  | [2, 5]             | [-1,1]        |
| hubRadius (%)      | [0.01, 0.25]       | [-0.05, 0.05] |
| proRadius (m)      | [0.01, 0.125]      | [-0.05, 0.05] |

### Airfoil Properties:
| parameter_name     | observation_space  | action_space  |
|---|---|---|
| pos (%)            | [0.0, 1.0]         | [-0.05, 0.05] |
| offsetx (m)        | [-0.5, 0.5]        | [-0.05, 0.05] |
| chord (m)          | [0.01, 0.25]       | [-0.05, 0.05] |
| twist              | [0.0, 45.0]        | [-5, 5]       |
| m[^2]                  | [0.01, 0.1]        | [-0.01, 0.01] |
| p[^2]                  | [0.1, 0.9]         | [-0.01, 0.01] |
| t[^2]                  | [0.1, 0.4]         | [-0.01, 0.01] |
[^1]: Reynolds number, dimensionless value that measures the ratio of inertial forces to viscous forces and descibes the degree of laminar or turbulent flow. Systems that operate at the same Reynolds number will have the same flow characteristics even if the fluid, speed and characteristic lengths vary.
[^2]: from NACA 4-digit Airfoil Standarts, respectively: max camber, position of max camber and thickness.
