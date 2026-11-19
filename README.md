# flatppl-astro-templates

[Function reference](docs/reference.md) · [Live example](https://live.flatppl.org/#model=https%3A%2F%2Fraw.githubusercontent.com%2Fflatppl-community%2Fflatppl-astro-templates%2Fmain%2Fexamples%2Fplayground.flatppl&target=Pi_post)

Spectral densities and quadrature on supplied wavelength and sky grids. Library version **0.1**.

For scalar redshift $z>-1$ and luminosity distance $D_L>0$, evaluate the rest spectra at the shifted coordinates.

```math
F_\lambda(\lambda)=\frac{L_\lambda(\lambda/(1+z))}{4\pi D_L^2(1+z)},
\qquad
F_\nu(\nu)=\frac{(1+z)L_\nu((1+z)\nu)}{4\pi D_L^2}.
```

| Quantity | Formula |
|---|---|
| Dust transmission | $T_i=10^{-0.4A_i}$ for extinction $A_i\ge0$ in magnitudes |
| Expected photons | $C=\frac{t}{hc}\sum_i \lambda_i F_{\lambda,i}A_{\mathrm{eff},i}q_i$ |
| Energy flux in a band | $F_{\rm band}=\sum_i F_{\lambda,i}T_i q_i$ |
| Sky density | $S_i=I_i/\sum_j I_j\Omega_j$ per steradian |

```flatppl
flatppl_compat = "0.1"
astro = load_module("main.flatppl")
rest_wavelength = astro.redshift_wavelength([4e-7, 5e-7], 0.2)
transmission = astro.dust_transmission([0.2, 0.1])
```

Use consistent units and aligned vectors. The [spectrum and photometry example](examples/spectrum-photometry.flatppl) projects a supplied spectrum into photon counts.
