# FFXI Vanilla Macro & Equipset Notes

Most of the text and examples are translated from:

* **[マクロ覚書3 ～ equip と equipset ～](https://leaguemili.com/blog-entry-1692.html)**
* **[FF11マクロ研究所 (hamham-fenrir.github.io/macroweb/)](https://hamham-fenrir.github.io/macroweb/)**


## FFXI Macro Guide: Wait Times, Equipment Commands, and Duplicate Items

### Advantage of /equip:

> No wait restrictions. Disadvantage: Limited number of equipment changes. To use different equipment with the same name, you must store them separately: Storage locations are specified by half-width numbers. 0: My Bag 1: Mog Wardrobe 1 2: Mog Wardrobe 2 3: Mog Wardrobe 3 4: Mog Wardrobe 4. No specification: Find the target equipment name in the order 0 1 2 3 4 and specify the first one you hit.


### The `/equipset` Command

* **Advantage:** Changes your entire gear set (up to 16 slots) in a single macro line. It can also successfully differentiate between duplicate items even if they are stored within the same wardrobe.
* **Disadvantage:** Imposes a mandatory **1-second cooldown** delay before another equipment set can be executed.
* **Logging:** To log the execution of an equipset in your chat log, add a space and type `echo` after the set number (e.g., `/equipset 1 echo`).

---

## Understanding `<wait>` and `/wait`

The `/wait` command (or the `<wait>` pronoun) inserts a specific delay between macro lines.

### Actual Delay Timings

Because the FFXI server communication interval (tick rate) operates on roughly a 0.4-second (or 0.33-second) cycle, there is a slight discrepancy between the input `wait` value and the actual in-game delay:

* `<wait 1>` = ~1.2 seconds
* `<wait 2>` = ~2.0 seconds
* `<wait 3>` = ~3.2 seconds
* `<wait 4>` = ~4.0 seconds
* `<wait 5>` = ~5.2 seconds
* `<wait 6>` = ~6.0 seconds

> ⚠️ *Note: Values over 60 or decimal values (e.g., 1.5) are not recognized by the game client.*

Using the standalone `/wait` command consumes an entire macro line, so it is rarely used. Instead, append the `<wait>` pronoun to the end of a text command, separated by a half-width space.

* **Example:** `/ws "Fast Blade" <t> <wait 1>`
* *Meaning:* Initiates the Fast Blade animation and waits roughly 1.2 seconds before executing the next line of the macro.



### Using `<wait>` Without a Value

If you use `<wait>` without specifying a number, the macro will pause only until the next line is recognized by the game client. This delay can be even shorter than a `<wait 1>`.

While this method is too unpredictable for precise gear swapping, it is highly effective for rapidly spamming job abilities (JAs), as it offers a slight speed increase.

---

## Why Wait Control is Necessary

When changing equipment to cast spells, activate abilities, or execute Weapon Skills, precision timing is required. If your wait times are poorly optimized, the macro will error out or fail to execute as intended.

While a standard 6-line macro naturally executes from top to bottom with a microscopic delay between each line, this native delay is static, extremely brief, and cannot be adjusted by the text command itself. Therefore, you must manually define your wait times.

### Beware of Network Lag

You must always factor server lag into your macro timings.

For instance, consider a spell with a 2-second casting time using the following macro sequence:

1. `/equipset 5` (Precast/Fast Cast Gear)
2. `/ma "Cure III" <t> <wait 2>`
3. `/equipset 1` (Idle/Defensive Gear)

If the server experiences a minor spike in lag, the spell might actually land *after* line 3 executes, causing your spell to land in your Idle gear instead of your Midcast/Potency gear.

Changing the delay to `<wait 3>` ensures a safer buffer. While it feels a bit slower, it guarantees that your spell benefits from your specialized gear sets regardless of network instability.

> 💡 **The Golden Rule:** The primary goal of a macro is to execute exactly as intended. Do not sacrifice mechanical accuracy in pursuit of shaving off a fraction of a second.


## Distinguishing between uses

At first glance, `/equip` may seem unnecessary, but frequent use of `/equipset` leads to frequent errors caused by the `wait 1` limit.
Basically, it's best to prioritize using `/equip` and use `/equipset` when the macro runs out of rows.

If the magic casting time for the Fastcast equipment set falls below 1 WAIT time, the magic effect enhancement equipment set will no longer be reflected.
In this case, you can apply Fastcast with `/equip` and Magic Effect Up with `/equipset`, reflecting both effects.

---


Here is the optimized English translation of your second notebook entry. I have polished the text to read naturally for an English-speaking audience, preserved the technical accuracy of the FFXI server ticks, formatted the raw data into a clean Markdown table, and updated the Twitter references to modern "X" terminology.

---

## FFXI Macro Guide: Why Wait Times Are Inconsistent

* **Published:** 2020/12/21 | **Updated:** 2026/01/07

The `<wait>` command is vital for controlling our macros by introducing necessary delays. However, the actual processing time for a given wait value is not a fixed constant. This guide explains why that happens and how to optimize for it.

---

## FFXI's 0.417-Second Server Tick Rate

According to research shared by FFXI player @funanz on X (formerly Twitter), 
Final Fantasy XI communicates with the server in rigid intervals of **0.417 seconds**.

> 🔗 **Reference Link:** [Original X Thread by @funanz](https://twitter.com/funanz/status/1339548696392843265)

**When you use a `<wait>` command to control a delay, the game cannot process it at the exact second specified.** Instead, it *rounds your action to the nearest server tick*, creating a **potential discrepancy of up to 0.417 seconds** (with the exception of wait values that are multiples of 5). Knowing this rule changes how we build our gearswaps.

---

### Server Processing Windows by Wait Value

| Wait Value | Minimum Delay (sec) | Maximum Delay (sec) |
| --- | --- | --- |
| **1** | 0.833 | 1.250 |
| **2** | 1.667 | 2.083 |
| **3** | 2.917 | 3.333 |
| **4** | 3.750 | 4.167 |
| **5** | **5.000** | **5.000** |
| **6** | 5.833 | 6.250 |
| **7** | 6.667 | 7.083 |
| **8** | 7.917 | 8.333 |
| **9** | 8.750 | 9.167 |
| **10** | **10.000** | **10.000** |

> ⚠️ *Note: Because client performance and hardware frame rates vary, actual real-world values may differ slightly from user to user.*

---

## Practical Example

Consider this defensive Paladin macro:

```text
/equipset 17 (React Gear)
/ma "React" <me> <wait 1>
/ja "Palisade" <me>
/equip back "Moonlight Cape"
/equipset 8 (Palisade / Defensive Gear)
```

This macro is built to cast React in `equipset 17`. 
If React is on cooldown, it *automatically moves down the lines to activate Palisade in `equipset 8` instead*.

The **base casting time** of React is **1.0 second**. 
The delay between transmitting `/ma "React"` and transmitting the next line is defined by `<wait 1>`. 
Therefore, React *must* finish casting completely within that `<wait 1>` window.

Because the server ticks every 0.417 seconds, a `<wait 1>` will actually process at either **0.833 seconds** or **1.250 seconds**. To guarantee that React always finishes casting in time, the *cast duration must be compressed below the minimum threshold of 0.833 seconds*. This mathematically requires a minimum of **17% Fast Cast**.

### The Client Factor

In reality, raw math isn't enough because local hardware lag plays a role. You cannot just aim for exactly 0.833 seconds and expect it to work perfectly. You must **test your macros repeatedly in your own gameplay environment to find your sweet spot**. 
Some failures only occur once every 20 casts or under specific combat conditions.

* In the above blog writer's environment, a 20% Fast Cast setup still occasionally failed. They bumped it up to **22% FC (bringing the cast time down to 0.78 seconds)** and it is now stable.
* For @funanz (who conducted the original tick research), their macros stopped failing entirely once they pushed the cast time down to **0.76 seconds**.

---

## Fast Cast (FC) Idle Gear Failures & Workarounds

Due to how the game queues commands, if you build a macro that immediately swaps from **Fast Cast idle sets** into high-potency midcast gear *without* using a wait line, it will occasionally glitch and fail to register the midcast equipment.

* **Trigger Condition:** Occurs on spells where the total casting time drops **below 0.603 seconds**.
* **Fix 1:** Change your target to `<st>` (e.g., `/ma "Cure III" <st>`). *Note: Using `<lastst>` will not fix the issue.*
* **Fix 2:** Adjust your gear to deliberately keep your casting time at **0.603 seconds or higher**.
* **Fix 3:** Simply recast the spell manually if it fails *(only recommended if the spell has a fast recast time and low consequences).*

### Recommendation

For the vast majority of players, **Fix 1** is the cleanest solution.

However, if you dislike the extra stroke (or controller input) required by the sub-target menu, or if you play a Tank job where sitting in vulnerable Fast Cast gear for a fraction of a second poses a lethal risk, you should design your sets around **Fix 2** or **Fix 3**.

> 🔗 **Deep Dive:** [See this follow-up X thread by @funanz for the full breakdown.](https://x.com/funanz/status/1547521535283720192)

As modern FFXI gameplay has accelerated, we cast spells far more frequently, and our casting speeds are incomparably faster than they were in the past. 
As things get faster, macro control becomes significantly harder. 
Because modern individual gear pieces hold so much stat power, failing a gearswap hurts your performance more than ever before. 
What used to be a negligible millisecond error in the past is now a major optimization problem we have to account for.

---

### Recast timers

`<recast>` or `/recast`

You can display the cooldown time via chat with "/p <recast=ability <b10>name or magic name>". Basically, it is used when it is necessary to relay tactical information like `Mewing Lullaby` cooldowns. It's often used in Scholar strategems, Corsair wildcards, and random deals.

Unlike `/recast`, it is possible to display multiple recasts on a single line. However, too much information can sometimes hinder communication. Although it does not directly lead to action, it becomes a macro that indirectly helps from the perspective of planning.

---

## Why Go Back to Vanilla?

Lua scripts offer infinite options that standard in-game `/equipset` commands cannot perfectly replicate.

While lua scripting is psychologically validated by **Social Proof** ("everyone uses it") and **Authority** ("the experts say it's required"), if we are honest, it has always existed in a strict grey zone.

More importantly, Japanese players since the PS2 era have proven for decades that you can play at the absolute highest level without relying on external tools. 
To me, this automation is being pushed to hard by the community and makes me feel disconnected from the core spirit of the game. 

If you ever find yourself spending more time in Visual Studio Code than in the actual game, you know exactly what I mean.

The Vanilla macro approach is:

* **100% Legit:** Zero risk of account penalties or breaking the Terms of Service.
* **Update-Proof:** Your macros will never break or crash when the game client receives a version update.
* **Bilingual Flexibility:** If necessary, you can write the macros (although there are traps like <Assault> meaning the event, not the pet ability) that switch between the Japanese and English game clients if you enjoy playing the game in both languages.
* **In-Game Efficiency and Immersion:** Swap new gear pieces into your equipsets and review changes instantly in-place, rather than ALT+TAB and constantly editing and reloading text scripts.
* **Server-Side Security:** By using vanilla mechanics, your equipsets and macros are securely saved directly on the official FFXI servers.
