# 🍩 &nbsp;Rust core features

Finally, we are here

<br />

We all had known Rust is fast but <span style="font-size: 40px; color: red;">WHY????</span>

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

## 🍩 &nbsp;Ownership system

<br />

Try to answer following questions:

1. Where the variable `x` exist? (stack memory or heap memory?) 
2. How much memory use of the `x`?
3. When the `x` memory will be collection。

::right::

<div style="height: 100%; display: flex; flex-direction: column; justify-content: center;">

<br />

```js{2|3-4|all}
function main() {
    let x = [1, 2, 3];
    let y = x;
    let z = y;

    console.log(x, y, z);
}
```

<br />

</div>

<!-- 
    Part 3.1: Ownership system
-->

---
level: 2
layout: two-cols
---

## 🍩 &nbsp;Rust version

<div style="height: 70%; display: flex; flex-direction: column; justify-content: center;">

Lets's see the rust version:

<br />

```rs
fu main() {
    let x = vec![1, 2, 3];
    let y = x;
    let z = y;

    println!("{}, {}, {}", x, y, z);
}
```

</div>

::right::

<br />

<v-clicks>

1. It's almost same as JavaScript version, so it's easy to understand
2. I can surely explain what happened under the hood 
3. I can say the code is safe with great conviction

</v-clicks>

<!--
    Part 3.2: Explain why rust is the better choice!
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
layout: intro
---

## 🔐 &nbsp;Rust is also safe and easy to use

<br />

I think it's time to show you the Rust code.

<!--
    Part 3.4: Rust is safe and friendly

    example: enum, Option, panic, rust-analyzer...
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
    Part 3.5: Other topic for Rust
-->
