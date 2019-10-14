# tcoast (Transport Along Coast)


| Travis CI (Python 3.6) | Read the Docs | Code Coverage |
|:----------------------:|:-------------:|:-------------:|
|  |  |  |

**Python 3**

This module computes the transport along perpendicular vectors to the coast. 
The processing of the data is done through `xarray`. For more information 
refer to ReadTheDocs

## Get the code:

1. Make a new directory where you want the repository.
1. Clone the **tcoast** repository from Github. In the command prompt, type:
`git clone https://github.com/Josue-Martinez-Moreno/tcoast.git`
1. Install the package globally:
`pip install -e .`
This make the package an editable install so that it can be updated with future 
additions to **tcoast**. To instead install the package locally:
`pip install --user .`

## Update the code:

1. Move into your **tcoast**  directory.
1. Update your GitHub repository.
`git pull`
1. Edit your install of **tcoast** .
`pip install -e .` 
or
`pip install --force-reinstall -e .`
or, for local installation: 
`pip install --ignore-installed --user .`

## Test the code:

Execute:
pytest -m tcoasts --cov=tcoasts

## Maths:

This code computes the transport along perpendicular vectors to the coast.

Perpendicular vectors are computed using the coastline slopes. Normal 
vectors are computed at the center of each interpolated cell (Figure 1) and the
interpolated velocity is projected over the normal by using the scalar projection 
property of dot products:

![Alt Text](https://github.com/Josue-Martinez-Moreno/tcoast/blob/master/figures/p_vectors.png "Perpendicular Vectors")

\begin{equation}
    \vec(u)\cdot\hat{n} = u*cos(\theta) + v*sin(\theta)
\end{equation}

Then the new projected velocity vector corresponds to:

\begin{equation}
    \vec(u) = \left[\vec(u)\cdot\hat{n}\right]\cdot\hat{n}
\end{equation}

Then the transport is computed using:

\begin{equation}
    T = \int \int u dxdz
\end{equation}

Additional constrains can be added in which the transport will be masked 
by tracers. For example, figure 2 shows the transport of passive tracers at the 
Gulf of Mexico with concentrations larger than 10% ($C_0 = 1 mol/m^3$). 

![Alt Text](https://github.com/Josue-Martinez-Moreno/tcoast/blob/master/figures/t_ptracers.png "Perpendicular Vectors")