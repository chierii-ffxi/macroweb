# 🏹 Ranged Attack & Weapon Skills

Macros for Ranger (`RNG`) utilizing pre-cast Snapshot gear and clean Midshot transitions.
A second macro button returns us to the TP base gear if meleeing.

## Standard Ranged Attack Execution

Two phases of a ranged attack:
1. **Pre-cast (Snapshot):** Reduces the initial aiming delay.
2. **Midshot (Chakutama / Landing):** Swaps into your Store TP / Ranged Attack gear right before the bullet hits the target.

### Version 1

```addon
/equipset 160 echo [Snapshot]
/range <stnpc>
/equipset 152 echo [Chakutama]
```

But this is not really good because hitting the <stnpc> confirm button too quickly can still result in the next line not being executed.

### Version 2

Alternatively without using an equipset for Snapshot: https://usapo.amausa.net/archives/3055

```addon
/equip back Ambuscade Cape [ベレナスケープ(Snapshot +10)]
/equip body AMカバン+2
/equip head [テーオンシャポー(Snapshot +10)]
/equip legs [ORブラッカエ+3(Snapshot +15)]
/ra <stnpc> (or even <t>)
/equipset 152 [Chakutama]
```

The goal is to hit the Snapshot cap (70) at the moment the shot is fired:

- Merits +10
- With upper manual macro +35
- Other gear +25 (here the trick is to idle already in sufficient snapshot gear so that the few lines above get us to the cap)
- Total +60（with magic +70）

## Ranged Weapon Skill (Magic/Agility Scaling)

Optimized for physical (such as `Last Stand` or elemental WS output (such as `Trueflight`).
In this example, for `Trueflight`, we can swap in Agility, Magic Attack Bonus (MAB), and Weapon Skill Damage (WSD) gear.

```addon
/equipset 158 echo [Magic WS]
/weaponskill "Trueflight" <t> <wait>
/equipset 155 echo [Engaged TP]
```

> ⚠️ **Note:** I had always put <wait Number> in the WS macro. But after reading hte JP sites, it seems a raw `<wait>` without a specified integer value works fine. I tested this and it seems to work well, also confirmed here: https://www.reddit.com/r/ffxi/comments/wb5eha/wait_in_ws_macros/

# 🏹 Instant Pull Variant (Since claiming King Behemoth is important in 2026)

This macro bypasses a full Snapshot `/equipset` and `<stnpc>` to avoid system delays.
Instead manually swaps three key pieces instantly upon weapon firing, immediately followed by the Midshot (Chakutama) landing set.

```addon
/equip head "Taeon Chapeau"
/equip hands "Ikenga Gloves"
/equip feet "Meganatada Jambeaux +2"
/range <t>
/equipset 173 echo [Midshot]
```

