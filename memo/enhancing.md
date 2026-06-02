## Standard Enhancing Magic

Spells with standard casting times where a pre-cast Fast Cast set safely transitions into the full duration/potency midcast set.
This setup is very inconsistent as explained in the README file. Try to avoid:

```addon
/equipset 48 echo [FastCast]
/ma Stoneskin <me> <wait 1>
/equipset 50 <wait 4> echo [Enhancing]
/equipset 44 echo [AfterCast]
```

Instead: either use manual pieces with /equip commands or idle in (partial) Fast Cast gear to have Fast Cast already equipped when the macro (spell) starts. Example (here /equipset 101 is mixed idle / Fast Cast gear):

```addon
【/equip】 【胴】 【ピンガチュニック+1】
【/equip】 【両脚】 【ピンガズボン+1】
【/equip】 【両手】 【ファナチクグローブ】
/ma 【ストンスキン】 <me> <stpt>
【/equipset】 111 echo 【ストンスキン】 <wait 7>
【/equipset】 101 echo 待機
```

English example:

```addon
/equip body "Inyanga Jubbah +2"
/ma Haste <stpt>
/equipset 50 <wait 4> echo [Enhancing]
/equipset 44 echo [AfterCast]
```

JP example: 

```addon
【/equip】 【胴】 【ピンガチュニック+1】
【/equip】 【両脚】 【ピンガズボン+1】
【/equip】 【両手】 【ファナチクグローブ】
/ma 【ヘイスト】 <stpt>
【/equipset】 110 echo 汎用強化 <wait 3>
【/equipset】 101 echo 待機
```

---

## Very Short Spells

Use case: When the base casting speed is so rapid that it is not actually necessary to equip additional fast cast gear at all.

```addon
/ma "Protect II" <me>
/equipset 50 <wait 2> echo [Enhancing]
/equipset 44 echo [AfterCast]
```
