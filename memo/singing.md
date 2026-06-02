## Dummy Song

Dummy 1 (English):

```addon
/echo [Uta Tsuika +1]
/equipset 131 echo [Daurdabla]
/ma "Scoop's Operetta" <stpt>
```

Dummy 1 (JP):

```addon
/echo ◇◇◇歌枠追加１◇◇◇
【/equipset】 22 echo 【ダウルダヴラ】
/ma 【戦士】達の【ピーアン】VI <stpt>
```

Dummy 2

```addon
/echo [Uta Tsuika +2]
/equipset 131 echo [Daurdabla]
/ma "Sheepfoe Mambo" <stpt>
```

Dummy 2 (JP):

```addon
/echo ◇◇◇歌枠追加２◇◇◇
【/equipset】 22 echo 【ダウルダヴラ】
/ma 【戦士】達の【ピーアン】V <stpt>
```

Combined dummy 1+2 songs:

```addon
【/equipset】 22 echo 【ダウルダヴラ】
/ma 【戦士】達の【ピーアン】VI <me> <wait 5>
/ma 【戦士】達の【ピーアン】V <me> <wait 2>
【/equipset】 29 echo 【ファストキャスト】待機移動
【/echo】 ◇◇◇【ファストキャスト】待機移動
```

Song Effect/Duration

English Example (here BRD uses a lot of fast-cast pieces in the idle set, so can go straight to singing):

```addon
/ma "Valor Minuet V" <stpt>
/equipset 129 echo [Song Effect]
/equip feet "Brioso Slippers +3" <wait 3>
/equipset 140 echo [Idle in fast cast set]
```

JP example:

```addon
/ma 猛者の【メヌエット】V <stpt>
【/equipset】 27 echo メヌマチマドマンボカロエチュ
【/equip】 【両足】 【ブリオソスリッパー】 <wait 2>
【/equipset】 29 echo 【ファストキャスト】待機移動
【/echo】 ◇◇◇【ファストキャスト】待機移動
```

Honor March:

```addon
【/equip】 【レンジウェポン】 【マルシュアス】 <wait>
【/recast】 栄典の戴冠【マーチ】
/ma 栄典の戴冠【マーチ】 <stpt>
【/equipset】 38 echo 栄典マチ専用 <wait 2>
【/equipset】 29 echo 【ファストキャスト】待機移動
【/echo】 ◇◇◇【ファストキャスト】待機移動
```

Horde Lullaby (1 has higher range):

```adddon
【/equip】 【レンジウェポン】 【ブラーハープ+1】
【/equipset】 30 echo 【ララバイ】
/ma 魔物達の【ララバイ】 <t>
```

Minne for the tank:

```addon
/ma 重装騎兵の【ミンネ】V <stpt>
【/equipset】 24 echo バラシルダーミンネ
【/equip】 【両脚】 【ムセスサラウィル+1】 <wait 2>
【/equipset】 29 echo 【ファストキャスト】待機移動
【/echo】 ◇◇◇【ファストキャスト】待機移動
```

Debuff (Finale, Elegy):

```addon
【/equip】 【レンジウェポン】 【ギャッラルホルン】
【/equipset】 28 echo 敵歌共通
/ma 修羅の【エレジー】 <t>
```


### Job Abilities

## Clarion Call

JP example (communication only, no gear to swap in, can also omit this macro and just select the /jobability from menu):

```addon
/p ◇◇◇【クラリオンコール】使います◇◇◇
/ja 【クラリオンコール】 <me> <stpt>
```

## Pianissimo

Also no gear relevant:

```addon
/ja 【ピアニッシモ】 <me>
```

## Nitro (combined macro)

JP example:

```addon
/p ◇【ナイチンゲール】＆【トルバドゥール】
【/equip】 【両足】 【ＢＩスリッパー+4】
【/equip】 【胴】 【ＢＩジュストコル+4】
/ja 【ナイチンゲール】 <me> <wait 1>
/ja 【トルバドゥール】 <me>
```

I prefer making 2 separate macros and structuring them as `[Ni` and `tro]` on the macro bar. 

## Marcato

```addon
【/recast】 マルカート
/ja マルカート <me>
【/equip】 【レンジウェポン】 【マルシュアス】 <wait>
```

## Soul Voice

```addon
/p ◇◇◇【ソウルボイス】使います◇◇◇
【/equip】 【両脚】 【ＢＩキャニオンズ+3】
/ja 【ソウルボイス】 <me> <stpt>
```

### Others

Wake-me-up via stage 1 prime weapon:

```addon
【/equip】 【レンジウェポン】 【ラックナシェード】
【/echo】 ◇◇◇【ラックナシェード】◇◇◇
```

Mazurka, Daurdabla-only (no modifiers):

```addon
【/equipset】 22 echo 【ダウルダヴラ】
/ma 【チョコボ】の【マズルカ】 <stpt>
```
