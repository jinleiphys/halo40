---
theme: ./nucl-th
layout: cover
title: "SMOOTHIE: A Computational Tool for Nonelastic Breakup Calculations using the Ichimura-Austern-Vincent Formalism"
authors:
  - "Jin Lei": ["School of Physics Science and Engineering, Tongji University, Shanghai 200092, China."]
meeting: "International Symposium Commemorating the 40th Anniversary of the Halo Nuclei (HALO-40), Beijing, October 12–18, 2025."
meetingShort: "HALO-40"
date: "October 16, 2025"
# preTitle: "Advances in"
---

<div class="absolute top-0 left-0 w-full h-full" style="z-index: -1;">
  <img src="/pics/background.png" class="opacity-20" style="position: absolute; top: 0; left: 0; width: auto; height: auto; max-width: 50%; max-height: 50%;" />
</div>



---

# Outline

<div class="mt-12 space-y-5 text-2xl">

1. **Motivation** - Breakup reactions in nuclear physics

2. **Breakup Classification** - Exclusive vs. Inclusive breakup

3. **Theoretical Framework** - Ichimura-Austern-Vincent (IAV) formalism

4. **SMOOTHIE Code** - Implementation and features

5. **Applications** - Three case studies demonstrating the code

6. **Summary** - Key results and future directions

</div>

---

# The Reaction of Two-Body Structured Projectile

<div class="grid grid-cols-2 gap-6 h-96">
  <div class="text-center">
    <img src="/pics/reaction.png" class="w-full h-full object-contain mb-2">
  </div>
  <div class="grid grid-rows-4 gap-4">
    <div v-click>
      <div class="text-left space-y-1">
        <p class="text-xl" style="color: #0FA3B1;">• Extract optical potential, rms radius, density distributions</p>
      </div>
    </div>
    <div v-click>
      <div class="text-left space-y-1">
        <p class="text-xl" style="color: #0FA3B1;">• Extract spin, parity, spectroscopic factors example: <sup>132</sup>Sn(d,p)<sup>133</sup>Sn</p>
      </div>
    </div>
    <div v-click>
      <div class="text-left space-y-1">
        <p class="text-xl" style="color: #0FA3B1;">• Study nuclear dynamics properties of halo nuclei</p>
      </div>
    </div>
    <div v-click>
      <div class="text-left space-y-1">
        <p class="text-xl" style="color: #0FA3B1;">• Provide energy for star burning synthesis of elements</p>
      </div>
    </div>
  </div>
</div>

<div v-click class="text-center" style="margin-top: -1rem;">
  <p class="text-2xl" style="color: #146b8c;">
    <strong>Breakup reaction is very important:</strong><br>
    provides both dynamics information and weakly bound projectile properties
  </p>
</div>

---

# Breakup Classification

<div class="text-center mt-8">
  <p class="text-3xl" style="color: #0FA3B1;">From the experimental point of view, breakup can be classified into two different types</p>
</div>

<div class="grid grid-cols-2 gap-8 mt-12">
  <div class="text-center">
    <p class="text-2xl font-bold mb-4" style="color: #0FA3B1;">Exclusive Breakup</p>
    <img src="/pics/exclusive.png" class="w-full h-64 object-contain">
  </div>
  <div class="text-center">
    <p class="text-2xl font-bold mb-4" style="color: #0FA3B1;">Inclusive Breakup</p>
    <img src="/pics/inclusive.png" class="w-full h-64 object-contain">
  </div>
</div>

---

# Exclusive Breakup

• Take <sup>6</sup>Li as an example

<div class="text-center">
  <img src="/pics/dA_chans_exclusive.png" class="w-full h-96 object-contain">
</div>

---

# Inclusive Breakup

• Take <sup>6</sup>Li as an example

<div class="text-center">
  <img src="/pics/dA_chans_inclusive.png" class="w-full h-96 object-contain">
</div>

---

# Study of Inclusive Breakup

The study of inclusive breakup can be used to understand the following subjects:

<div class="grid grid-cols-3 gap-4 mt-4">
  <div class="text-center">
    <p class="text-lg font-bold mb-2" style="color: #0FA3B1;">Inclusive Spectrum</p>
    <img src="/pics/Li6inclusive.png" class="w-full h-48 object-contain">
    <div class="text-sm mt-2 space-y-1 flex flex-col justify-center" style="min-height: 4.5rem;">
      <p>Clear α band dominates</p>
      <p>Suggests nonelastic processes</p>
    </div>
  </div>
  <div v-click class="text-center">
    <p class="text-lg font-bold mb-2" style="color: #0FA3B1;">Surrogate Reaction</p>
    <img src="/pics/surrogate.png" class="w-full h-48 object-contain">
    <div class="text-sm mt-2 space-y-1 flex flex-col justify-center" style="min-height: 4.5rem;">
      <p>• Study compound nucleus</p>
      <p>• Formation and decay processes</p>
    </div>
  </div>
  <div v-click class="text-center">
    <p class="text-lg font-bold mb-2" style="color: #0FA3B1;">Knockout Reaction</p>
    <img src="/pics/knockout.png" class="w-full h-48 object-contain">
    <div class="text-sm mt-2 space-y-1">
      <p>• Study Spectroscopic factor</p>
      <p>• Mostly based on Eikonal approximation</p>
      <p>• Fully quantum model needed</p>
    </div>
  </div>
</div>

---

# The Ichimura-Austern-Vincent (IAV) Model

• Fully quantum mechanical model for breakup reactions

<p style="color: #808080;"><em>M. Ichimura, N. Austern, and C. M. Vincent, PRC 32, 431 (1985)</em></p>

<div class="mt-4">

• **Inclusive breakup:**
$$
a + A \to b + B^* , \quad \text{where } a = b + x
$$

</div>

<div v-click class="mt-4">

• **IAV Nonelastic breakup (NEB):**
  $$
  \frac{d^2\sigma}{dE_b d\Omega_b}\Big|_\mathrm{NEB}= -\frac{2}{\hbar v_a} \rho_b(E_b)
  \langle \color{#c90024}{G_x^{(+)}\rho(\vec{k}_b)} \color{black}{|W_x|}  \color{#c90024}{G_x^{(+)}\rho(\vec{k}_b)} \color{black}{\rangle}
  $$

</div>

<div v-click class="ml-8">

  • where $\color{#c90024}{G_x^{(+)}\rho(\vec{k}_b)}$: wave function in $x+A$ channel

</div>

<div v-click class="ml-8">

  • $\rho(\vec{k}_b)$: source term ($x$ from $a$), $\langle \vec{r}_x | \rho(\vec{k}_b)\rangle =  \langle \vec{r}_x \chi_b^{(-)} | V | \Psi^{(+)} \rangle$

</div>

<div v-click class="ml-8">

  • DWBA approximation: $\Psi^{(+)} \approx \chi_a^{(+)} \phi_a$

</div>

---

# SMOOTHIE Code

<span style="color: #FF8C00;">**S**</span>cattering <span style="color: #FF8C00;">**M**</span>odel of <span style="color: #FF8C00;">**O**</span>ptical <span style="color: #FF8C00;">**O**</span>perator <span style="color: #FF8C00;">**Th**</span>eory for <span style="color: #FF8C00;">**I**</span>chimura-Austern-Vincent <span style="color: #FF8C00;">**E**</span>quations

<div class="absolute bottom-20 right-8 w-120">
  <img src="/pics/Generator.png" class="w-full h-auto object-contain rounded-lg shadow-lg border border-gray-300">
</div>

<div class="mt-6">

**Key Features:**
- Modern Fortran implementation of IAV formalism
- Calculates nonelastic breakup cross sections
- Supports multiple optical potential models
- Web-based input generator available

</div>

<div v-click class="mt-6">

**Availability:**
- Website: [smoothie.fewbody.com](https://smoothie.fewbody.com)
- Open source (MIT License)
- Platform: Linux, macOS, Windows

</div>

---

# SMOOTHIE Implementation

<div class="grid gap-8" style="grid-template-columns: 1fr 1.5fr;">

<div>

**Key Features:**
- Advanced IAV formalism
- Lagrange-mesh R-matrix
- Green's function approach
- Intrinsic spins support
- HPC optimized

</div>

<div v-click>

**Modular Architecture:**
- **general_modules/** - Precision, constants, systems, channels
- **mesh_modules/** - Numerical integration, Gaussian quadrature
- **pot_modules/** - Woods-Saxon, KD02, CH89, external files
- **pw_modules/** - Partial wave decomposition: Coulomb functions, spherical harmonics, Clebsch-Gordan coefficients
- **cm2lab/** - Center-of-mass to lab frame conversion

</div>

</div>

---

# Application 1: Halo-Induced Reactions

**Reaction:** $^{11}$Be + $^{64}$Zn at $E_{\text{lab}}$ = 28.7 MeV

<div class="mb-4 text-lg">
Study of neutron halo effects in <sup>11</sup>Be on inclusive <sup>10</sup>Be production
</div>

<div class="grid grid-cols-2 gap-6 mt-4">
  <div class="text-center">
    <img src="/pics/be11zn_dsdwc_n2.png" class="w-full h-80 object-contain">
  </div>
  <div v-click class="text-center">
    <img src="/pics/dsdwde_n2_cdcc.png" class="w-full h-80 object-contain">
  </div>
</div>

<div class="mt-1 text-sm" style="color: #808080;">
A. Di Pietro, A.M. Moro, Jin Lei and R. de Diego, Physics Letters B 798, 134954 (2019)
</div>

---

# Application 2: Surrogate Reactions

**Reaction:** $^{238}$U(d,p) to study fission probabilities of n+$^{238}$U

<div class="mb-3 text-base">
Use (d,pX) reaction to populate <sup>239</sup>U states and measure fission decay
</div>

<div class="grid grid-cols-2 gap-8 mt-4">
  <div>
    <img src="/pics/dp_surrogate.png" class="w-full h-auto">
    <p class="text-sm text-center mt-2">Fission probability vs excitation energy</p>
  </div>
  <div>

Corrected fission probability:

$$
P_\chi^{\mathrm{corr}}\left(E^*\right)=\frac{P_\chi^{\mathrm{meas}}\left(E^*\right) \sigma_{\mathrm{TB}}\left(E^*\right)}{\sigma_{\mathrm{BF}}\left(E^*\right)}
$$

where:

<div class="ml-4">

- $P_\chi^{\mathrm{meas}}$: Measured fission probability
- $\sigma_{\mathrm{TB}}$: Total breakup cross section
- $\sigma_{\mathrm{BF}}$: Breakup-fusion cross section

</div>

<div class="mt-4 text-sm" style="color: #808080;">

Q. Ducasse, et al., Phys. Rev. C 94, 024614 (2016)

</div>

  </div>
</div>

---

# Application 3: Knockout Reactions



<div class="grid grid-cols-2 gap-8 mt-4">
  <div class="flex flex-col justify-center">
    <p class="text-xl mb-4"><strong>One nucleon breakup reactions:</strong></p>
    <div class="ml-6 space-y-2 text-lg">
      <p>• <sup>14</sup>O at 53A MeV on <sup>9</sup>Be target</p>
      <p>• <sup>16</sup>C at 75A MeV on <sup>9</sup>Be target</p>
    </div>
    <div class="mt-6 space-y-2">
      <p><strong>Key results:</strong></p>
      <p>• Agreement with experimental data</p>
      <p>• Validates quantum treatment vs. eikonal approximation</p>
      <p>• Extract spectroscopic factors</p>
    </div>
    <div class="mt-6 text-sm" style="color: #808080;">
      Jin Lei and Angela Bonaccorso, Physics Letters B 813, 136032 (2021)
    </div>
  </div>
  <div class="flex items-center">
    <img src="/pics/knock_com_data.png" class="w-full object-contain" style="max-height: 425px;">
  </div>
</div>

---

# Summary

<div class="mt-8 space-y-6 text-xl">

**Theoretical Framework**

<div class="ml-6">

- IAV formalism provides fully quantum treatment of inclusive breakup
- Accounts for projectile structure and reaction dynamics

</div>

<div v-click class="mt-6">

**SMOOTHIE Implementation**

<div class="ml-6">

- Modern, open-source tool with modular architecture
- Efficient numerical methods for practical calculations

</div>

</div>

<div v-click class="mt-6">

**Validated Applications**

<div class="ml-6">

- Halo-induced reactions: <sup>11</sup>Be + <sup>64</sup>Zn
- Surrogate reactions: <sup>238</sup>U(d,p) fission studies
- Knockout reactions: <sup>14</sup>O and <sup>16</sup>C at intermediate energies

</div>

</div>

</div>

<div v-click class="mt-8 text-center text-2xl" style="color: #0FA3B1;">

**SMOOTHIE is ready for your breakup reaction calculations!**

</div>

---

# Acknowledgments

<div class="absolute top-4 right-4 w-74">
  <img src="/logo.png" alt="Logo">
</div>

### Collaborator:
- **Antonio M. Moro** (Universidad de Sevilla)

### Funding Support:
- National Natural Science Foundation of China
- Fundamental Research Funds for the Central Universities

<div class="text-center mt-4 text-3xl" style="color:#4A9CF7;">
Thank you for your attention!
</div>

<div class="text-center mt-2 text-xl">
Questions and discussions are welcome
</div>

<div class="text-center mt-2 text-lg">
  <p class="mb-1"><strong>SMOOTHIE Code:</strong> <a href="https://smoothie.fewbody.com" style="color: #0FA3B1;">smoothie.fewbody.com</a></p>
  <p class="mb-1"><strong>Research Group:</strong> <a href="https://www.fewbody.com" style="color: #0FA3B1;">www.fewbody.com</a></p>
  <p class="mb-1"><strong>Contact:</strong> <a href="mailto:jinlei@fewbody.com" style="color: #0FA3B1;">jinlei@fewbody.com</a></p>
</div>
