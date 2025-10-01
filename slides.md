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
  <img src="/pics/dA_chans_inclusive.png" class="w-full h-72 object-contain">
</div>

<div class="mt-2 space-y-1">
  <p v-click class="text-lg" style="color: #0FA3B1;"><strong>EBU (Elastic Breakup):</strong> Can be treated in the standard three-body model such as Faddeev/CDCC</p>
  <p v-click class="text-lg" style="color: #FF6B35;"><strong>NEB (Nonelastic Breakup):</strong> Needs special treatment</p>
</div>

---

# Navigation

Hover on the bottom-left corner to see the navigation's controls panel

## Keyboard Shortcuts

|     |     |
| --- | --- |
| <kbd>space</kbd> / <kbd>tab</kbd> / <kbd>right</kbd> | next animation or slide |
| <kbd>left</kbd>  / <kbd>shift</kbd><kbd>space</kbd> | previous animation or slide |
| <kbd>up</kbd> | previous slide |
| <kbd>down</kbd> | next slide |

---
layout: image-right
image: https://cover.sli.dev
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

### Collaborators:
- **Antonio M. Moro** (Universidad de Sevilla)

### Funding Support:
- National Natural Science Foundation of China
- Fundamental Research Funds for the Central Universities

<div v-click class="text-center mt-4 text-3xl" style="color:#4A9CF7;">
Thank you for your attention!
</div>

<div v-click class="text-center mt-2 text-xl">
Questions and discussions are welcome
</div>

<div class="text-center mt-2 text-lg">
  <p class="mb-1"><strong>SMOOTHIE Code:</strong> <a href="https://smoothie.fewbody.com" style="color: #0FA3B1;">smoothie.fewbody.com</a></p>
  <p class="mb-1"><strong>Research Group:</strong> <a href="https://www.fewbody.com" style="color: #0FA3B1;">www.fewbody.com</a></p>
  <p class="mb-1"><strong>Contact:</strong> <a href="mailto:jinlei@fewbody.com" style="color: #0FA3B1;">jinlei@fewbody.com</a></p>
</div>
