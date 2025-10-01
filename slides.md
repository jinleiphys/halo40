---
theme: ./nucl-th
layout: cover
title: "SMOOTHIE: A Computational Tool for Nonelastic Breakup Calculations using the Ichimura-Austern-Vincent Formalism"
authors:
  - "Jin Lei": ["School of Physics Science and Engineering, Tongji University, Shanghai 200092, China."]
meeting: "International Symposium Commemorating the 40th Anniversary of the Halo Nuclei (HALO-40), Beijing, October 12–18, 2025."
meetingShort: "HALO-40"
# preTitle: "Advances in"
---

<div class="absolute top-0 left-0 w-full h-full" style="z-index: -1;">
  <img src="/pics/background.png" class="opacity-20" style="position: absolute; top: 0; left: 0; width: auto; height: auto; max-width: 50%; max-height: 50%;" />
</div>



---

# The reaction of two body structured projectile

<div class="grid grid-cols-2 gap-6 h-96">
  <div class="text-center">
    <img src="/pics/reaction.png" class="w-full h-full object-contain mb-2">
  </div>
  <div class="grid grid-rows-4 gap-4">
    <div v-click>
      <div class="text-left space-y-1">
        <p class="text-xl" style="color: #EA33F0;">Extract optical potential, rms radius, density distributions</p>
      </div>
    </div>
    <div v-click>
      <div class="text-left space-y-1">
        <p class="text-xl" style="color: #EA33F0;">Extract spin, parity, spectroscopic factors example: <sup>132</sup>Sn(d,p)<sup>133</sup>Sn</p>
      </div>
    </div>
    <div v-click>
      <div class="text-left space-y-1">
        <p class="text-xl" style="color: #EA33F0;">Study nuclear dynamics properties of halo nuclei</p>
      </div>
    </div>
    <div v-click>
      <div class="text-left space-y-1">
        <p class="text-xl" style="color: #4A9CF7;">Provide energy for star burning synthesis of elements</p>
      </div>
    </div>
  </div>
</div>

<div v-click class="text-center" style="margin-top: -1rem;">
  <p class="text-2xl" style="color: #FF6B35;">
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
    <p class="text-2xl font-bold mb-4" style="color: #EA33F0;">Exclusive Breakup</p>
    <img src="/pics/exclusive.png" class="w-full h-64 object-contain">
  </div>
  <div class="text-center">
    <p class="text-2xl font-bold mb-4" style="color: #EA33F0;">Inclusive Breakup</p>
    <img src="/pics/inclusive.png" class="w-full h-64 object-contain">
  </div>
</div>

---

# Exclusive Breakup

- Take 6Li as an example

<div class="text-center">
  <img src="/pics/dA_chans_exclusive.png" class="w-full h-96 object-contain">
</div>

---

# Inclusive Breakup

- Take 6Li as an example

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
    <p class="text-lg font-bold mb-2" style="color: #EA33F0;">Surrogate Reaction</p>
    <img src="/pics/surrogate.png" class="w-full h-48 object-contain">
    <div class="text-sm mt-2 space-y-1 flex flex-col justify-center" style="min-height: 4.5rem;">
      <p>Study compound nucleus</p>
      <p>Formation and decay processes</p>
    </div>
  </div>
  <div v-click class="text-center">
    <p class="text-lg font-bold mb-2" style="color: #FF6B35;">Knockout Reaction</p>
    <img src="/pics/knockout.png" class="w-full h-48 object-contain">
    <div class="text-sm mt-2 space-y-1">
      <p>Study Spectroscopic factor</p>
      <p>Mostly based on Eikonal approximation</p>
      <p>Fully quantum model needed</p>
    </div>
  </div>
</div>

---

# The Ichimura-Austern-Vincent (IAV) Model

- Fully quantum mechanical model for breakup reactions

<p style="color: #808080;"><em>M. Ichimura, N. Austern, and C. M. Vincent, PRC 32, 431 (1985)</em></p>

<div class="mt-4">

- **Inclusive breakup:**
$$
a + A \to b + B^* , \quad \text{where } a = b + x
$$

</div>

<div v-click class="mt-4">

- **IAV Nonelastic breakup (NEB):**
  $$
  \frac{d^2\sigma}{dE_b d\Omega_b}\Big|_\mathrm{NEB}= -\frac{2}{\hbar v_a} \rho_b(E_b)
  \langle \color{#c90024}{G_x^{(+)}\rho(\vec{k}_b)} \color{black}{|W_x|}  \color{#c90024}{G_x^{(+)}\rho(\vec{k}_b)} \color{black}{\rangle}
  $$

</div>

<div v-click class="ml-8">

  - where $\color{#c90024}{G_x^{(+)}\rho(\vec{k}_b)}$: wave function in $x+A$ channel

</div>

<div v-click class="ml-8">

  - $\rho(\vec{k}_b)$: source term ($x$ from $a$), $\langle \vec{r}_x | \rho(\vec{k}_b)\rangle =  \langle \vec{r}_x \chi_b^{(-)} | V | \Psi^{(+)} \rangle$

</div>

<div v-click class="ml-8">

  - DWBA approximation: $\Psi^{(+)} \approx \chi_a^{(+)} \phi_a$

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

# Code

Use code snippets and get the highlighting directly!

```ts
interface User {
  id: number
  firstName: string
  lastName: string
  role: string
}

function updateUser(id: number, update: Partial<User>) {
  const user = getUser(id)
  const newUser = { ...user, ...update }
  saveUser(id, newUser)
}
```

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
