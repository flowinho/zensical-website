---
title: "LoL: Wild Rift"
icon: lucide/swords
hide:
- footer
---

## Wild Rift Ranked Season 19

### Tabellarische Übersicht

|Lane  |Kill|Death|Assist|Ratio|
|:-----|:--:|:---:|:----:|----:|
|ADC   |48  |28   |54    |3.28 |
|Supp  |0   |2    |16    |8.0  |
|Mid   |2   |6    |6     |1.4  |
|Jungle|0   |0    |0     |0.0  |
|Top   |0   |0    |0     |0.0  |

Formel um die KDA Ratio zu berechnen:

$$
r=\frac{k+a}{d}
$$


### Stats pro Lane

<div class="grid" markdown>


```mermaid
pie 
    "ADC" : 6
    "Mid" : 1
    "Supp" : 1
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
  curve a["ADC"]{48, 28, 54}
  curve m["Mid"]{2, 6, 6}
  curve s["Supp"]{0, 2, 16}

  max 45
  min 0
```

</div>

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
  curve w["Win"]{5, 1, 0, 0, 0}
  curve l["Loss"]{2, 0, 1, 0, 0}

  max 5
  min 0
```

### Champion-Verteilung pro Lane

```mermaid
sankey-beta
  ADC, Caitlyn, 5
  ADC, Ezreal, 2
  Mid, Kayle, 1
  Supp, Lux, 1
``` 

