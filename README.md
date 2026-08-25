# Development and Verification of a Four-Node Plane-Strain Neo-Hookean User Element

## Project Overview

This project develops and verifies a four-node quadrilateral User Element (UEL)
for a compressible Neo-Hookean solid under plane-strain conditions.

The formulation is developed using the Total Lagrangian approach and implemented
as a Fortran UEL in Abaqus. The implementation is verified using a four-element
displacement-controlled patch test and an independent analytical solution
implemented in MATLAB.

## Objectives

- Develop a four-node quadrilateral finite element for finite-strain elasticity.
- Implement a compressible Neo-Hookean constitutive model.
- Formulate the element using the Total Lagrangian description.
- Derive the elemental residual vector and consistent tangent matrix.
- Implement the formulation as an Abaqus UEL using Fortran.
- Perform a four-element patch test.
- Verify the UEL results against an analytical homogeneous solution.
- Validate the stress response using MATLAB.

## Key Features

- Four-node quadrilateral element
- Two translational degrees of freedom per node
- Four Gauss integration points
- Plane-strain formulation
- Compressible Neo-Hookean material
- Total Lagrangian formulation
- Consistent material tangent
- Abaqus UEL implementation
- MATLAB analytical verification

## Material Model

The compressible Neo-Hookean strain-energy density is

W(F) = μ/2 (I₁ - 3 - 2 ln J) + κ/2 (J - 1)²

where:

- μ = 2.0 MPa
- κ = 5.0 MPa
- I₁ = tr(FᵀF)
- J = det(F)

The first Piola-Kirchhoff stress is

P = μ(F - F⁻ᵀ) + κJ(J - 1)F⁻ᵀ

The Cauchy stress is obtained from

σ = (1/J) P Fᵀ

## Finite Element Formulation

The element uses four-node isoparametric interpolation with four-point
Gauss integration.

The elemental internal residual is calculated from

rₑ = ∫ Gᵀp dV

and the consistent tangent matrix is

Kₑ = ∫ GᵀDG dV

All integrations are performed over the undeformed reference configuration.

## Patch Test

A 2 mm × 2 mm square domain is divided into four quadrilateral elements.

### Boundary Conditions

- Left boundary: horizontal displacement fixed
- Bottom boundary: vertical displacement fixed
- Right boundary: prescribed uniform horizontal displacement

The displacement history is

uR(t) = 0.1t mm

with

0 ≤ t ≤ 1

The final displacement is:

uR = 0.100 mm

corresponding to a final engineering strain of 5%.

## Analytical Verification

The MATLAB program calculates the analytical homogeneous Neo-Hookean
response for each prescribed displacement.

The following quantities are calculated:

- λ₁
- λ₂
- J
- First Piola-Kirchhoff stress
- Cauchy stress
- σ₁₁
- σ₂₂

The MATLAB analytical solution is compared with the Abaqus UEL response.

## Results

At the final right-boundary displacement of 0.100 mm:

| Quantity | Result |
|---|---:|
| λ₁ | 1.050000 |
| λ₂ | 0.97257 |
| J | 1.0212 |
| P₁₁ | 0.298310 MPa |
| Analytical σ₁₁ | ≈ 0.306720 MPa |
| Abaqus UEL σ₁₁ | 0.306724 MPa |
| Relative difference | ≈ 0.0013% |

The Abaqus UEL response and MATLAB analytical response overlap over the
complete loading range, demonstrating consistency between the finite-element
implementation and the analytical constitutive solution.

## Project Workflow

1. Develop finite-strain kinematics.
2. Define the Neo-Hookean constitutive model.
3. Derive the first Piola-Kirchhoff stress.
4. Derive the consistent material tangent.
5. Develop the four-node isoparametric element.
6. Implement Gauss integration.
7. Implement the formulation in the Abaqus UEL.
8. Perform the four-element patch test.
9. Develop the analytical solution in MATLAB.
10. Compare Abaqus UEL results with MATLAB results.
11. Evaluate the numerical error.

## Software Used

- Abaqus
- Fortran
- MATLAB

## Files Included

- `neo.for` – Fortran Abaqus UEL implementation
- `mat.m` – MATLAB analytical verification code
- `patch.inp` – Abaqus patch-test input file
- `Indrajit_Das_NeoHookean_UEL_Project.pdf` – Detailed project report

## Conclusion

The four-node plane-strain Neo-Hookean UEL successfully reproduces the
homogeneous deformation response of the four-element patch test.

The close agreement between the Abaqus UEL result and the independent MATLAB
analytical solution verifies the stress calculation and demonstrates the
consistency of the implemented finite-element formulation.

## Author

**Indrajit Das**

M.Tech Student  
Department of Mechanical Engineering  
Indian Institute of Technology Kanpur

August 2026# Neo-Hookean-UEL-FEM-project
Development and Verification of a Four-Node Plane-Strain Neo-Hookean User Element
