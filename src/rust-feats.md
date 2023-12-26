# 🍩 &nbsp;Rust core features

Finally, we are here

<br />

We all had known Rust is fast 

<v-click>

but <span style="font-size: 40px; color: red;">WHY????</span>

</v-click>

<br />

<v-click>

<img src="/img/why.jpeg" style="margin: 0 auto;" />

</v-click>

<br />

<v-click>

let me try to explain

</v-click>

<!--
    Part 3. Rust core features
-->

---
level: 2
layout: two-cols
---

## 😶‍🌫️ &nbsp;Strong Type & Ownership - JS

<div style="height: 80%; display: flex; flex-direction: column; justify-content: center;">

```js{all|2|3|4|6|all}
function main() {
    let s = [1, 2, 3];
    let t = s;
    let u = t;

    console.log(s, t, u);
}
```
</div>

::right::

<br />

Try to answer following questions:

<br />

<v-clicks>

1. Where the variable `s` exist? (stack memory or heap memory?) 
2. How much memory use of the `s`?
3. When the `s` memory will be collection。

</v-clicks>

<!-- 
    Part 3.1: JavaScript code is difficult to figure out what happened under the hook
-->

---
level: 2
layout: two-cols
---

## 😶‍🌫️ &nbsp;Strong Type & Ownership - Rust

<div style="height: 70%; display: flex; flex-direction: column; justify-content: center;">

Lets's see the rust version:

<br />

```rs
fu main() {
    let s: Vec<i8> = vec![1, 2, 3];
    let t = s;
    let u = t;

    println!("{:?}, {:?}, {:?}", s, t, u);
    // <-- dealloc here
}
```

</div>

::right::

<br />
<br />
<br />

<v-clicks>

1. It's almost same as JavaScript version, so it's easy to understand
2. I can surely explain what happened under the hood 
3. I can say the code is safe with great conviction

</v-clicks>

<!--
    Part 3.2: Why Rust is fantastic!
-->

---
level: 2
layout: intro
---

## 🍩 &nbsp;Memory management

<br />

There are two camps of memory management:

1. Manual memory management camp: C, C++, etc -> <span style="color: red;">NO SAFE</span>
2. Automated memory management: Java, JavaScript, etc -> <span style="color: red;">SLOW (GC)</span>

<v-click>

But, here appears the third camp 🎉:

</v-click>

<br />

<v-click>

<p style="font-size: 34px;">Rust -- Automatic memory management but no GC!</p>

</v-click>

<!--
    Part 3.3: Memory management: the core reason why rust is fast
-->

---
level: 2 
layout: two-cols 
---

## Python memory management

<img src="/img/py-represent.jpg" style="height: 70%; margin: 22px; object-fit: contain;" />

::right::

<img src="/img/py-assigning.jpg" style="height: 70%; margin-bottom: 12px; object-fit: contain;" />

> 🔗 img sourcc: 《Programming Rust 2nd》p86-87

<!-- 
    Part 3.4: Memory management for py

    explain what's python handle heap memory
-->

---
level: 2 
layout: two-cols 
---

## C memory management

<img src="/img/c-represent.jpg" style="height: 70%; margin: 22px; object-fit: contain;" />

::right::

<img src="/img/c-assigning.jpg" style="height: 70%; margin-bottom: 12px; object-fit: contain;" />

> 🔗 img sourcc: 《Programming Rust 2nd》p88

<!-- 
    Part 3.5: Memory management for c

    explain what's c handle heap memory
-->

---
level: 2 
layout: two-cols 
---

## Rust memory management

<img src="/img/rs-represent.jpg" style="height: 70%; margin: 22px; object-fit: contain;" />

::right::

<img src="/img/rs-assigning.jpg" style="height: 70%; margin-bottom: 12px; object-fit: contain;" />

> 🔗 img sourcc: 《Programming Rust 2nd》p88

<!-- 
    Part 3.6: Memory management for Rust 

    explain what's rust handle heap memory
-->

---
level: 2
layout: intro
---

## 🤔 Why Rust design is better?

<br />

1. Prevent the **use after free** error in C
2. Prevent loop reference in JS or Python

<br />

<v-click>

In other words:

</v-click>

<v-click>

Rust is a <span style="color: red; font-size: 24px; font-weight: bolder;">MEMORY SAFE</span> language!

</v-click>

<!--
    Part 3.7: Rust is a memory safe language
-->

---
level: 2
layout: intro
---

## 🔐 &nbsp;Rust is not only safe but also a friendly language

<br />

I think it's time to show you the Rust code.

Let's code a simple program:

1. create a enmu type `Fruits`;
2. log fruit name by inputing argument;
3. use `switch` statement by default;

<!--
    Part 3.8: Rust is safe and friendly

    Rust:

    1. run `cargo new hello-rust && cd $_`
    2. run `vi ./src/main.rs` to coding

    TypeScript:

    1. run `mkdir bye-ts && cd $_`
    2. run `npm init -y` init npm package
    3. run `npm install -D typescript ts-node` install dev dependencies
    4. run `npx tsc --init` generate tsconfig.json file
    5. run `vi index.ts` to coding 
-->

---
level: 2
layout: two-cols
---

## 🔦 &nbsp;Other features

<br />

1. **concurrence**
2. struct, trait
3. crates & modules
3. iterator
4. etc...

::right::

<div style="height: 100%; display: flex; flex-direction: column; justify-content: center;">

> All computers are now parrallel...
> 
> Parallel programming **is** programming.
>
> -- Michael McCool et al., Structured Parallel Programming

</div>

<!--
    Part 3.9: Other topic for Rust
-->
