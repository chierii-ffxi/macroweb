# FFXI Summoner (SMN) Blood Pact Optimizations

## 📊 Blood Pact Recast Calculations

The target is to hit the absolute lowest recast time using a combination of Blood Pact 
Delay gear tiers and avatar favors.

* **BP Delay I:** Caps at **-15s**. (e.g., my current gear when I wrote these macros: Head -8, Legs -7, Hands -6 = Capped)
* **BP Delay II:** : -10s total (Sancus Satchet HQ -7, Apo. Dalmatica HQ -3).
* **BP Delay III:** : -10s total
* **Current Passive Total:** **-35s** base gear reduction.

*Note: Achieving a theoretical -40s maximum is possible but requires optimization of SMN Magic Skill sets.*

* [BG-Wiki Comprehensive SMN Guide](https://www.bg-wiki.com/ffxi/The_Heretical_Art:_Comprehensive_Summoner_Guide)
* [BG-Wiki Blood Pact Delay Mechanics](https://www.bg-wiki.com/ffxi/Blood_Pact_Ability_Delay)

---

## 🔮 Blood Pact Ward (Buffs / Utilities)

> ⚠️ Avatar's Favor should be active.

English example:

```addon
/echo <recast="Blood pact: Ward"> [Recast]
/equipset 47 <wait 0> echo [BPdelay-]
/pet "Hastega II" <stpt> <wait>
/equipset 49 <wait 2> echo [WardBP+]
/echo <recast="Blood pact: Ward"> [Recast]
/equipset 44 echo [Aftercast: Acc/Favor/Perpetuation]
```

JP example:

```addon
【/echo】 <recast=【契約の履行:幻術】> <recast=【契約の履行:験術】>
【/equipset】 117 echo 履行短縮
【/pet】 【ヘイスガ】II <stpt> <wait>
【/equipset】 118 echo スキル <wait>
【/echo】 <recast=【契約の履行:幻術】> <recast=【契約の履行:験術】>
【/equipset】 116 echo 命中・維持軽減・加護
```

*Examples for testing:* `Hastega II`, `Fleet Wind`, `Rolling Thunder` etc.

---

## ⚡ Blood Pact Rage (Nukes / Physical Attacks)

Timing windows are adjusted to ensure mid-cast multiplier gear swaps register perfectly before the blood pact hits the target.

English example:

```addon
/echo <recast="Blood pact: Rage"> [Recast]
/equipset 47 <wait 0> echo [BPdelay-]
/pet "Histeric Assault" <t> <wait>
/equipset 46 <wait 4>
/echo <recast="Blood pact: Rage"> [Recast]
/equipset 44 echo [Aftercast: Acc/Favor/Perpetuation]
```

JP example:

```addon
【/echo】 <recast=【契約の履行:幻術】> <recast=【契約の履行:験術】>
【/equipset】 117 echo 履行短縮
【/pet】 【ヒステリックアサルト】 <t> <wait>
【/equipset】 119 echo 物理履行 <wait>
【/echo】 <recast=【契約の履行:幻術】> <recast=【契約の履行:験術】>
【/equipset】 116 echo 命中・維持軽減・加護
```

*Examples for testing:* `Thunderspark`, `Volt Strike` etc.
