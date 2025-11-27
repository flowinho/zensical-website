---
title: "LoL: Wild Rift"
icon: lucide/swords
hide:
- footer
---

## Wild Rift Ranked Season 19

### Tabellarische Übersicht

|Lane  |Kill|Death|Assist|Ratio|Win|Loss|%   |
|:-----|:--:|:---:|:----:|----:|:-:|:--:|:--:|
|ADC   |77  |47   |75    |3.23 |7  |3   |70% |
|Supp  |0   |2    |16    |8.0  |1  |0   |100%|
|Mid   |2   |6    |6     |1.4  |0  |1   |0%  |
|Jungle|0   |0    |0     |0.0  |0  |0   |0%  |
|Top   |7   |3    |3     |3.3  |1  |0   |100%  |


### Stats pro Lane

<div class="grid" markdown>


```mermaid
pie 
    "ADC" : 9
    "Mid" : 1
    "Supp" : 1
    "Top" : 1
```

```mermaid
---
config:
  radar:
    width: 250
    height: 250
---
radar-beta
  axis k["Kills"], d["Deaths"], a["Assists"]
  curve a["ADC"]{77, 47,  65}
  curve m["Mid"]{2,   6,  6}
  curve s["Supp"]{0,  2,  16}
  curve t["Top"]{7,   3,  3}

  max 80
  min 0
``` 
</div>


```mermaid
xychart-beta 
	title "KDA Ratio pro Lane"
	x-axis [ADC, Supp, Mid, Jungle, Top]
	y-axis "K/D/A Ratio"
	bar [3.23,8,0,0,3.3]
```

### Win-Loss pro Lane

```mermaid
---
config:
  radar:
    width: 250
    height: 250
---
radar-beta
  axis a["ADC"], s["Supp"], m["Mid"], j["Jungle"], t["Top"]
  curve w["Win"]{7, 2, 0, 0, 1}
  curve l["Loss"]{3, 0, 1, 0, 0}

  max 7
  min 0
```

### Champion-Verteilung pro Lane

```mermaid
sankey-beta
  ADC, Caitlyn, 6
  ADC, Ezreal, 4
  Mid, Kayle, 1
  Supp, Lux, 1
  Top, Kayle, 1
``` 