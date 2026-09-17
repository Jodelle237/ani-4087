Casque choisi : Meta Quest 3

Le Meta Quest 3 possède un champ de vision annoncé d’environ 110° horizontal × 96° vertical par œil, selon la documentation officielle de Meta.

Dans OpenXR, le champ de vision est décrit par quatre angles : angleLeft, angleRight, angleUp et angleDown. En prenant une approximation symétrique de ces valeurs, on obtient :

* angleLeft = −55°
* angleRight = +55°
* angleUp = +48°
* angleDown = −48°

Source : documentation officielle Meta Horizon OS, « Panel resolution and display options » : https://developers.meta.com/horizon/documentation/spatial-sdk/spatial-sdk-2dpanel-resolution/

Conséquence d’un champ symétrique de même surface : le champ de vision conserverait la même surface totale, mais sa répartition autour de l’axe central serait différente, ce qui pourrait déplacer les limites visibles par rapport au champ asymétrique réel.