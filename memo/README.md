# FFXI Vanilla Macro & Equipset Optimizations

The logic used in these macros are adapted from:

* **[FF11マクロ研究所 (hamham-fenrir.github.io/macroweb/)](https://hamham-fenrir.github.io/macroweb/)**
* **[マクロ覚書3 ～ equip と equipset ～](https://leaguemili.com/blog-entry-1692.html)**

## Explanation on wait durations, slot names, and how to equip one of multiple items with the same name (Ambuscade capes)

### Advantage of /equip:

> No wait restrictions. Disadvantage: Limited number of equipment changes. To use different equipment with the same name, you must store them separately: Storage locations are specified by half-width numbers. 0: My Bag 1: Mog Wardrobe 1 2: Mog Wardrobe 2 3: Mog Wardrobe 3 4: Mog Wardrobe 4. No specification: Find the target equipment name in the order 0 1 2 3 4 and specify the first one you hit.

### Advantage of /equipset:

> You can change equipment to about all in just one macro line. You can switch between equipment with the same name within the same storage.
Disadvantages: You need to wait 1 time between equipment sets.

To log the execution, leave a half-width space after the equipment set number and enter `echo`.

### wait

The command /wait or <wait> generates a specified number of waits between the macro lines.

```addon
wait 1 = about 1.2 seconds,
wait 2 = about 2.0 seconds,
wait 3 = about 3.2 seconds,
wait 4 = about 4.0 seconds,
wait 5 = about 5.2 seconds,
wait 6 = about 6.0 seconds
```

* The communication interval with the server is said to be 0.4 seconds (or 0.33 seconds), so there may be a slight discrepancy between the number of seconds specified by the wait value and the actual result.

## Distinguishing between uses

At first glance, `/equip` may seem unnecessary, but frequent use of `/equipset` leads to frequent errors caused by the `wait 1` limit.
Basically, it's best to prioritize using `/equip` and use `/equipset` when the macro runs out of rows.

If the magic casting time for the Fastcast equipment set falls below 1 WAIT time, the magic effect enhancement equipment set will no longer be reflected.
In this case, you can apply Fastcast with `/equip` and Magic Effect Up with `/equipset`, reflecting both effects.

---

## ⚖️ Why Go Back to Vanilla?

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
