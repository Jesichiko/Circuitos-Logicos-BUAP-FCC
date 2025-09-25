Un comparador booleano es un dispositivo electrónico que recibe números $a,b \in \mathbb{C} \ conjunto \ de \ trabajo$
tal que podemos usar los **operandos de equidad, in-equidad, etc en ellos**.

Por ejemplo, dados $\forall a,b \in\mathbb{N}:len(a) \wedge len(b) < 2 \ (base \ 2)$ podemos modelar un circuito con **funciones booleanas** (como en [[Display numérico]] o [[Sumadores booleanos]])  para usar **operandos en el conjunto de los naturales** (de 1 bit):

## Comparador de 1 bit

| $a$ | $b$ | $\|$ | $=$ | $\neq$ | $a>b$ | $a<b$ |
| --- | --- | ---- | --- | ------ | ----- | ----- |
| 0   | 0   |      | 1   | 0      | 0     | 0     |
| 0   | 1   |      | 0   | 1      | 0     | 1     |
| 1   | 0   |      | 0   | 1      | 1     | 0     |
| 1   | 1   |      | 1   | 0      | 0     | 0     |
Esto nos da como resultado las reglas de correspondencia:
$$f_==\bar{a}\bar{b}+ab$$
$$f_{\ne}=\bar{a}b+a\bar{b}$$
$$f_>=a\bar{b}$$
$$f_<=\bar{a}b$$
Para números naturales de 2 bits tenemos las siguientes **funciones booleanas**:

## Comparador de 2  bits

| $x(a_1)$ | $y(a_2)$ | $\|$ | $z(b_1)$ | $w(b_0)$ | $\|$ | $=$ | $\ne$ | $a>b$ | $a<b$ |
| -------- | -------- | ---- | -------- | -------- | ---- | --- | ----- | ----- | ----- |
| 0        | 0        |      | 0        | 0        |      | 1   | 0     | 0     | 0     |
| 0        | 0        |      | 0        | 1        |      | 0   | 1     | 0     | 1     |
| 0        | 0        |      | 1        | 0        |      | 0   | 1     | 0     | 1     |
| 0        | 0        |      | 1        | 1        |      | 0   | 1     | 0     | 1     |
| 0        | 1        |      | 0        | 0        |      | 0   | 1     | 1     | 0     |
| 0        | 1        |      | 0        | 1        |      | 1   | 0     | 0     | 0     |
| 0        | 1        |      | 1        | 0        |      | 0   | 1     | 0     | 1     |
| 0        | 1        |      | 1        | 1        |      | 0   | 1     | 0     | 1     |
| 1        | 0        |      | 0        | 0        |      | 0   | 1     | 1     | 0     |
| 1        | 0        |      | 0        | 1        |      | 0   | 1     | 1     | 0     |
| 1        | 0        |      | 1        | 0        |      | 1   | 0     | 0     | 0     |
| 1        | 0        |      | 1        | 1        |      | 0   | 1     | 0     | 1     |
| 1        | 1        |      | 0        | 0        |      | 0   | 1     | 1     | 0     |
| 1        | 1        |      | 0        | 1        |      | 0   | 1     | 1     | 0     |
| 1        | 1        |      | 1        | 0        |      | 0   | 1     | 1     | 0     |
| 1        | 1        |      | 1        | 1        |      | 1   | 0     | 0     | 0     |
Las funciones resultantes son las siguientes:
$$1.f_==\bar{x}\bar{y}\bar{z}\bar{w}+\bar{x}y\bar{z}w+x\bar{y}z\bar{w}+xyzw$$
$$=\bar{x}\bar{z}(\bar{y}\bar{w}+yw)+xz(\bar{y}\bar{w}+yw)$$
$$=(\bar{x}\bar{z}+xz)(\bar{y}\bar{w}+yw)$$$$2.f_\ne=\bar{f_=}=\bar{(\bar{x}\bar{z}+xz)(\bar{y}\bar{w}+yw)}$$$$=\bar{(\bar{x}\bar{z}+xz)}+\bar{(\bar{y}\bar{w}+yw)}$$$$=(x\bar{z}+\bar{x}z)+(y\bar{w}+\bar{y}w)$$
$$3.f_>=\bar{x}y\bar{z}\bar{w}+x\bar{y}\bar{z}\bar{w}+x\bar{y}\bar{z}w+xy\bar{z}\bar{w}+xy\bar{z}w+xyz\bar{w}$$$$=\bar{z}\bar{w}(\bar{x}y+x\bar{y}+xy)+\bar{z}w(x\bar{y}+xy)+xyz\bar{w}$$
$$=\bar{z}\bar{w}(\bar{x}y+x)+\bar{z}w(x)+xyz\bar{w}$$
$$=\bar{x}y\bar{z}\bar{w}+x\bar{z}\bar{w}+x\bar{z}w+xyz\bar{w}$$
$$=\bar{x}y\bar{z}\bar{w}+x\bar{z}+xyz\bar{w}$$

$$4.f_<=\bar{x}\bar{y}\bar{z}w+\bar{x}\bar{y}z\bar{w}+\bar{x}\bar{y}zw+\bar{x}yz\bar{w}+\bar{x}yzw+x\bar{y}zw$$
$$=\bar{x}\bar{y}(\bar{z}w+z\bar{w}+zw)+\bar{x}y(z\bar{w}+zw)+x\bar{y}zw$$
$$=\bar{x}\bar{y}(\bar{z}w+z)+\bar{x}yz+x\bar{y}zw$$
$$=\bar{x}\bar{y}\bar{z}w+\bar{x}\bar{y}z+\bar{x}yz+x\bar{y}zw$$
$$=\bar{x}\bar{y}\bar{z}w+\bar{x}(\bar{y}z+yz)+x\bar{y}zw$$
$$=\bar{x}\bar{y}\bar{z}w+\bar{x}z+x\bar{y}zw$$
