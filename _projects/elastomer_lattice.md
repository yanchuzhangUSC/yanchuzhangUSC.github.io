---
title: ""
permalink: "/projects/elastomer_lattice/"
layout: single
author_profile: true
mathjax: true
---

# :star: ​Mechanics of Stretchy Elastomer Lattices

*Finite-deformation modeling of soft architected materials with extreme reversible stretchability.*

![Sequential stretching of a hierarchical elastomer lattice](/images/projects/elastomer_lattice/fig2c.png)

*Sequential stretching of a hierarchical elastomer lattice.*

## Project Overview

Stretchy elastomer lattices are lightweight architected materials that can undergo extremely large reversible deformation while maintaining structural integrity. Their mechanical response is governed not only by the hyperelastic behavior of the constituent elastomer, but also by the geometry, connectivity, and deformation modes of the lattice architecture.

In this project, I developed a theoretical framework to predict the finite deformation mechanics of elastomer lattices by connecting macroscopic lattice deformation with local beam stretching and rotation. The model captures both stretching and bending contributions and was validated against finite element simulations and experimental measurements.

## Modeling Framework

The model treats an elastomer lattice as a network of deformable beam ligaments. Under the affine deformation assumption, the local deformation of each beam is determined by the macroscopic deformation of the lattice unit cell. As illustrated below, two kinematic quantities are used to describe the dominant deformation mechanisms: the beam stretch \\(\hat{\lambda}\\) and the beam rotation angle \\(\hat{\theta}\\).

![Affine beam kinematics and deformation mechanisms](/images/projects/elastomer_lattice/fig5.png)

*Affine beam kinematics and the two dominant deformation mechanisms in elastomer lattices: axial stretching and bending/rotation.*

The local beam stretch is determined by the macroscopic deformation gradient,

$$
\hat{\lambda}
=
\sqrt{\mathbf{N}\cdot\mathbf{C}\mathbf{N}},
\qquad
\mathbf{C}
=
\mathbf{F}^{\top}\mathbf{F},
$$

where \\(\mathbf{F}\\) is the deformation gradient of the lattice unit cell, \\(\mathbf{C}\\) is the right Cauchy--Green tensor, and \\(\mathbf{N}\\) is the beam direction in the reference configuration.

The beam rotation angle is obtained from the angle between the reference beam direction and the current beam direction,

$$
\hat{\theta}
=
\cos^{-1}
\left(
\frac{\mathbf{N}\cdot\mathbf{F}\mathbf{N}}
{\sqrt{\mathbf{N}\cdot\mathbf{C}\mathbf{N}}}
\right).
$$

The lattice energy is then decomposed into stretching and bending contributions,

$$
W_{\mathrm{lattice}}
=
W_{\mathrm{stretch}}(\hat{\lambda})
+
W_{\mathrm{bend}}(\hat{\theta}).
$$

The stretching energy is associated with the axial elongation of the beam ligaments. In this framework, \\(W_{\mathrm{stretch}}\\) can be constructed from general hyperelastic constitutive models for the constituent elastomer, such as the neo-Hookean, Ogden, or Arruda--Boyce models. The bending energy is associated with beam rotation and is approximated using a linear rotational spring model.

Schematically, the two energy contributions can be written as

$$
W_{\mathrm{stretch}}
=
\sum_{\mathrm{beams}} \hat{W}(\hat{\lambda}),
\qquad
W_{\mathrm{bend}}
=
\sum_{\mathrm{joints}} \frac{1}{2}\beta \hat{\theta}^{2},
$$

where \\(\hat{W}(\hat{\lambda})\\) is the hyperelastic strain-energy density of a beam ligament and \\(\beta\\) is the rotational spring stiffness.

The resulting stress--deformation relation follows directly from the energy derivative, or for principal stretch-based descriptions,

$$
\mathbf{S}
=
\frac{\partial W_{\mathrm{lattice}}}{\partial \mathbf{F}},\qquad
s_i
=
\frac{\partial W_{\mathrm{lattice}}}{\partial \lambda_i}.
$$

## Numerical Simulation and Parametric Study

:pencil: ​**Effect of Constitutive Model**

The stretching energy of the beam ligaments can be constructed from different hyperelastic constitutive models. In the paper, I tested neo-Hookean, Ogden, and Arruda--Boyce models using the Octet-truss lattice as a representative architecture. The theoretical predictions agree well with ABAQUS finite element simulations for all three constitutive models, showing that the energy-based lattice framework can be coupled with different material laws.

![Effect of constitutive models on Octet-truss lattices](/images/projects/elastomer_lattice/fig9.png)

*Effect of constitutive models on the predicted stress--stretch response of Octet-truss elastomer lattices using different material models. (c) neo-Hookean. (d) Ogden. (e) Arruda--Boyce.*

:pencil: **Effect of Beam Radius**

The beam radius controls the lattice volume fraction and strongly affects the relative contribution of bending and stretching. For lattices with small beam radius, the bending contribution is relatively weak, and the stretching model alone can capture much of the response. As the beam radius increases, bending near the beam joints becomes more significant, especially during the early stage of deformation. Including the bending energy therefore improves the prediction accuracy for high-volume-fraction lattices.

![Effect of beam radius on Octahedral elastomer lattices](/images/projects/elastomer_lattice/fig10.png)

*Effect of beam radius on Octahedral elastomer lattices. Larger beam radius increases the importance of bending-induced stress during early deformation.*

To further interpret this behavior, I examined the stretching energy ratio, which quantifies the relative importance of stretching in the total lattice deformation energy. A low stretching-energy ratio indicates bending-dominated deformation, while a high stretching-energy ratio indicates stretching-dominated deformation. The results show that lattices may initially deform through bending and beam rotation, but gradually transition toward stretching-dominated behavior as the applied stretch increases.

![Stretching energy ratio and deformation-mode transition](/images/projects/elastomer_lattice/fig8.png)

*Stretching energy ratio of elastomer lattices, illustrating the transition from bending-dominated deformation at small stretch to stretching-dominated deformation at large stretch.*

This energy-ratio analysis also helps explain the beam-radius effect. For larger beam radius, bending contributes more strongly in the small-deformation regime, which is why the bending term becomes more important for accurately predicting the initial response. At larger stretch, the stretching energy ratio increases, indicating that the beam ligaments progressively align with the loading direction and axial stretching becomes the dominant mechanism.

:pencil: **Effect of Lattice Topology**

The model was further tested on different lattice topologies, including Octet-truss, Rhombic, and Octahedral lattices. When the beam radius is fixed, different topologies lead to different volume fractions and therefore different stiffness levels. When the volume fraction is fixed, the large-stretch responses become much closer, indicating that lattice topology mainly affects the early-stage bending-dominated regime, while the large-deformation response is increasingly governed by axial stretching of the beam ligaments.

![Effect of lattice topology on stress--stretch behavior](/images/projects/elastomer_lattice/fig11.png)

*Effect of lattice topology on the stress--stretch behavior of elastomer lattices. The comparison highlights the role of architecture in the transition from bending-dominated to stretching-dominated deformation.* (e) Same beam diameter. (f) Same volume fraction.

Overall, these numerical studies demonstrate that the proposed framework can capture the nonlinear mechanical behavior of elastomer lattices across different constitutive models, geometric parameters, and lattice topologies. 

## Hierarchical Lattices and Multiscale Stretchability

The same energy-based framework can be extended to hierarchical elastomer lattices with self-similar fractal architectures. In a hierarchical lattice, each beam ligament in a lower-order structure is replaced by a smaller lattice unit. As a result, the deformation is distributed across multiple structural orders rather than being imposed directly on the constituent elastomer.

![Breakdown of hierarchical Octahedral lattice](/images/projects/elastomer_lattice/fig4.png)

*Breakdown of a hierarchical Octahedral lattice from the macroscopic lattice structure to lower-order lattice units and finally to the elastomer network.*

To describe the deformation of an \(n\)-th order hierarchical lattice, I introduced the principal stretches of each hierarchical order as generalized coordinates,

$$
\mathbf{q}
=
\left(
{}^{(1)}\lambda_1,
{}^{(1)}\lambda_2,
{}^{(1)}\lambda_3,
\ldots,
{}^{(n)}\lambda_1,
{}^{(n)}\lambda_2,
{}^{(n)}\lambda_3
\right).
$$

For a given macroscopic stretch or loading condition, the deformation state of the hierarchical lattice is obtained by solving a constrained optimization problem,

$$
\mathbf{q}^{\ast}
=
\arg\min_{\mathbf{q}\in\mathbb{R}_{+}^{3n}}
{}^{(n)}\Pi(\mathbf{q}).
$$

The total potential energy of the \(n\)-th order hierarchical lattice is written as

$$
{}^{(n)}\Pi
=
{}^{(n)}W
+
{}^{(n)}V
-
U.
$$

Here, the stretching energy term accounts for the axial elongation of beam ligaments across the hierarchy,

$$
{}^{(n)}W
=
\sum_{\mathrm{orders}}
\sum_{\mathrm{beams}}
\hat{W}
\left(
{}^{(i)}\hat{\lambda}
\right),
$$

where the beam-level strain-energy function can be constructed from a hyperelastic constitutive model of the elastomer. The bending energy term accounts for beam rotation and joint-level flexural deformation,

$$
{}^{(n)}V
=
\sum_{\mathrm{orders}}
\sum_{\mathrm{joints}}
\frac{1}{2}
{}^{(i)}\beta
\left(
{}^{(i)}\hat{\theta}
\right)^2,
$$

where the bending contribution is approximated using a linear rotational spring model. The external loading contribution enters through the virtual work associated with the prescribed macroscopic uniaxial loading,

$$
\delta U
=
s_1 \delta\left(
{}^{(n)}\lambda_1\right).
$$

The optimization problem is solved subject to geometric compatibility constraints between neighboring hierarchical orders. For the Octahedral hierarchy, the stretch relation between two adjacent orders can be written as

$$
{}^{(i)}\lambda_1^2
=
\frac{1}{3}
{}^{(i+1)}\lambda_1^2
+
\frac{1}{3}
{}^{(i+1)}\lambda_2^2
+
\frac{1}{3}
{}^{(i+1)}\lambda_3^2.
$$

In addition, the lateral directions are traction-free under uniaxial loading. Therefore, each hierarchical order must satisfy stress-free lateral constraints,

$$
{}^{(i)}s_2
=
\frac{\partial {}^{(i)}\Pi}
{\partial {}^{(i)}\lambda_2}
=
0,
\qquad
{}^{(i)}s_3
=
\frac{\partial {}^{(i)}\Pi}
{\partial {}^{(i)}\lambda_3}
=
0.
$$

Together, the generalized coordinates, energy minimization, geometric compatibility constraints, and stress-free lateral constraints define the equilibrium deformation of the hierarchical lattice. This formulation explains how hierarchy delays local beam stretching: the macroscopic lattice can undergo very large deformation while the lower-order beam ligaments experience much smaller stretch.

The hierarchical model was validated against experimentally measured stress--stretch responses of the bulk elastomer, first-order Octahedral lattice, and second-order hierarchical Octahedral lattice. As shown below, the theoretical predictions capture the experimentally observed trend that increasing the hierarchical order reduces the initial stiffness and substantially increases the attainable macroscopic stretch. This behavior arises because deformation is distributed across multiple structural levels, allowing the lattice to rotate, unfold, and deform sequentially before the constituent elastomer beams approach their local stretch limit.

![Experimental validation of hierarchical elastomer lattices](/images/projects/elastomer_lattice/fig14.png){: width="85%" .align-center}

*Experimental validation of the stress--stretch response for hierarchical Octahedral elastomer lattices.*

## Studying Programmable Poisson's Ratio

Beyond predicting stress--stretch behavior, the same lattice-theory framework can also be used to estimate effective Poisson's ratios of architected elastomer metamaterials. This provides an additional validation case because the model is tested against experimentally reported 2D lattice designs with prescribed lateral deformation behavior.

For a uniaxially stretched lattice, the effective Poisson's ratio can be defined from the axial and transverse deformation as
$$
\nu_{\mathrm{eff}}
=
-
\frac{\varepsilon_{\mathrm{trans}}}
{\varepsilon_{\mathrm{axial}}}.
$$


In this case study, four 2D architected materials with target Poisson's ratios were modeled by approximating the curved or spiral beam members using equivalent straight-beam networks. The theoretical predictions were then compared with experimentally measured Poisson's ratios from the literature.

![Validation of programmable Poisson's ratio in 2D architected elastomer materials](/images/projects/elastomer_lattice/fig16.png)

*Validation of the proposed lattice model for 2D architected elastomer materials with programmable Poisson's ratios. The theoretical predictions agree well with experimentally reported values.*

This result shows that the proposed framework is not restricted to predicting uniaxial stress--stretch curves. By connecting macroscopic deformation to local beam stretch and rotation, the model can also capture effective deformation properties such as Poisson's ratio. This suggests that the theory can be used as a lightweight design tool for architected materials with prescribed nonlinear mechanical responses.

**[← Back to Project List](/projects/)**
