Un **display numérico** es un dispositivo electrónico para **representar números decimales.** Dependiendo de cuantos digitos pueda representar, la cantidad maxima de posibles combinaciones de estos aumenta.

El **display numérico de 7 segmentos** es el display más común para poder representar un dígito. Este está formado por **7 segmentos** que se pueden encender o apagar para formar distintos números. 

![[Pasted image 20250906234157.png]]

Estos segmentos están representados con **letras**:
![[Pasted image 20250906234551.png]]
 Podemos representar (como en [[Sumadores booleanos]]) un display de 7 segmentos con **funciones booleanas para representar cada numero único con combinaciones de entradas distintas**: 

Para **entradas binarias** que representen el número a mostrar podemos **crear funciones booleanas** que expresen con que combinaciones de entradas binario se tiene que prender. 

| $x$ | $y$ | $z$ | $w$ | $\|$ | $a$ | $b$ | $c$ | $d$ | $e$ | $f$ | $g$ | $pd$ |
| --- | --- | --- | --- | ---- | --- | :-- | --- | --- | --- | --- | --- | ---- |
| 0   | 0   | 0   | 0   |      | 1   | 1   | 1   | 1   | 1   | 1   | 0   | 0    |
| 0   | 0   | 0   | 1   |      | 0   | 1   | 1   | 0   | 0   | 0   | 0   | 0    |
| 0   | 0   | 1   | 0   |      | 1   | 1   | 0   | 1   | 1   | 0   | 1   | 0    |
| 0   | 0   | 1   | 1   |      | 1   | 1   | 1   | 1   | 0   | 0   | 1   | 0    |
| 0   | 1   | 0   | 0   |      | 0   | 1   | 1   | 0   | 0   | 1   | 1   | 0    |
| 0   | 1   | 0   | 1   |      | 1   | 0   | 1   | 1   | 0   | 1   | 1   | 0    |
| 0   | 1   | 1   | 0   |      | 0   | 0   | 1   | 1   | 1   | 1   | 1   | 0    |
| 0   | 1   | 1   | 1   |      | 1   | 1   | 1   | 0   | 0   | 0   | 1   | 0    |
| 1   | 0   | 0   | 0   |      | 1   | 1   | 1   | 1   | 1   | 1   | 1   | 0    |
| 1   | 0   | 0   | 1   |      | 1   | 1   | 1   | 0   | 0   | 1   | 1   | 0    |
| 1   | 0   | 1   | 0   |      | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 1    |
| 1   | 0   | 1   | 1   |      | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 1    |
| 1   | 1   | 0   | 0   |      | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 1    |
| 1   | 1   | 0   | 1   |      | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 1    |
| 1   | 1   | 1   | 0   |      | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 1    |
| 1   | 1   | 1   | 1   |      | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 1    |
Esto resulta en las funciones:
$f_a=\bar{x}\bar{y}\bar{w}+\bar{x}\bar{y}z+x\bar{y}\bar{z}+xy\bar{w}$

$f_b=\bar{x}\bar{y}+\bar{y}\bar{z}+\bar{x}zw+\bar{x}\bar{z}\bar{w}$

$f_c=\bar{x}w+\bar{x}y+\bar{y}\bar{z}$

$f_d=\bar{x}z\bar{w}+\bar{x}\bar{y}z+\bar{y}\bar{z}\bar{w}+\bar{x}y\bar{z}w$

$f_e=\bar{x}z\bar{w}+\bar{y}\bar{z}\bar{w}$

$f_f=x\bar{y}\bar{z}+\bar{x}y\bar{w}+\bar{x}y\bar{z}+\bar{x}\bar{z}\bar{w}$

$f_g=\bar{x}y+\bar{x}z+x\bar{y}\bar{z}$

$f_{pd}=xy+xz$
