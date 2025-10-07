Un **display numérico** es un dispositivo electrónico para **representar números decimales.** Dependiendo de cuantos digitos pueda representar, la cantidad maxima de posibles combinaciones de estos aumenta.

El **display numérico de 7 segmentos** es el display más común para poder representar un dígito. Este está formado por **7 segmentos** que se pueden encender o apagar para formar distintos números. 

![[Pasted image 20250906234157.png]]

Estos segmentos están representados con **letras**:
![[Pasted image 20250906234551.png]]
 Podemos representar (como en [[Sumadores booleanos]]) un display de 7 segmentos con **funciones booleanas para representar cada numero único con combinaciones de entradas distintas**: 

Para **entradas binarias** que representen el número a mostrar podemos **crear funciones booleanas** que expresen con que combinaciones de entradas binario se tiene que prender. 

| $w$ | $z$ | $y$ | $x$ | $\|$ | $a$ | $b$ | $c$ | $d$ | $e$ | $f$ | $g$ |
| --- | --- | --- | --- | ---- | --- | :-- | --- | --- | --- | --- | --- |
| 0   | 0   | 0   | 0   | $0$  | 1   | 1   | 1   | 1   | 1   | 1   | 0   |
| 0   | 0   | 0   | 1   | $1$  | 0   | 1   | 1   | 0   | 0   | 0   | 0   |
| 0   | 0   | 1   | 0   | $2$  | 1   | 1   | 0   | 1   | 1   | 0   | 1   |
| 0   | 0   | 1   | 1   | $3$  | 1   | 1   | 1   | 1   | 0   | 0   | 1   |
| 0   | 1   | 0   | 0   | $4$  | 0   | 1   | 1   | 0   | 0   | 1   | 1   |
| 0   | 1   | 0   | 1   | $5$  | 1   | 0   | 1   | 1   | 0   | 1   | 1   |
| 0   | 1   | 1   | 0   | $6$  | 1   | 0   | 1   | 1   | 1   | 1   | 1   |
| 0   | 1   | 1   | 1   | $7$  | 1   | 1   | 1   | 0   | 0   | 0   | 1   |
| 1   | 0   | 0   | 0   | $8$  | 1   | 1   | 1   | 1   | 1   | 1   | 1   |
| 1   | 0   | 0   | 1   | $9$  | 1   | 1   | 1   | 0   | 0   | 1   | 1   |
| 1   | 0   | 1   | 0   | $A$  | 1   | 1   | 1   | 0   | 1   | 1   | 1   |
| 1   | 0   | 1   | 1   | $B$  | 0   | 0   | 1   | 1   | 1   | 1   | 1   |
| 1   | 1   | 0   | 0   | $C$  | 1   | 0   | 0   | 1   | 1   | 1   | 0   |
| 1   | 1   | 0   | 1   | $D$  | 0   | 1   | 1   | 1   | 1   | 0   | 1   |
| 1   | 1   | 1   | 0   | $E$  | 1   | 0   | 0   | 1   | 1   | 1   | 1   |
| 1   | 1   | 1   | 1   | $F$  | 1   | 0   | 0   | 0   | 1   | 1   | 1   |
Esto resulta en las funciones:
$f_a = w + z\bar{y} + \bar{z}y + x$

$f_b = yx + zy + \bar{z}\bar{x} + w$

$f_c = \bar{y}x + z + w$

$f_d = w + \bar{z}\bar{y}x + zy + z\bar{x}$

$f_e = \bar{z}x + w(y + z)$

$f_f = \bar{y}\bar{x} + z\bar{y} + zx + wy$

$f_g = w + z(y + \bar{x}) + \bar{z}\bar{y}\bar{x}$

Esto podemos verlo como **modulos en Verilog** para una placa ****
```verilog
module display7seg (
    input wire w, z, y, x,
    output wire a, b, c, d, e, f, g
);
    assign a = w | (z & ~y) | (~z & y) | x;
    assign b = (y & x) | (z & y) | (~z & ~x) | w;
    assign c = (~y & x) | z | w;
    assign d = w | (~z & ~y & x) | (z & y) | (z & ~x);
    assign e = (~z & x) | (w & (y | z));
    assign f = (~y & ~x) | (z & ~y) | (z & x) | (w & y);
    assign g = w | (z & (y | ~x)) | (~z & ~y & ~x);
endmodule

```

en el **top-level** tenemos:
```verilog
module top_display_un_numero (
    input wire [3:0] num,   //hexa
    output wire [6:0] seg,  // segmentos
    output wire [3:0] an    // seleccion del display
);
	// segmentos
    wire a, b, c, d, e, f, g;

    // dividimos los 4 bits en w,z,y,x
    display7seg disp(
        .w(num[3]),
        .z(num[2]),
        .y(num[1]),
        .x(num[0]),
        .a(a),
        .b(b),
        .c(c),
        .d(d),
        .e(e),
        .f(f),
        .g(g)
    );

    assign seg = ~{a,b,c,d,e,f,g};

    // encendemos solo el display más a la derecha
    assign an = 4'b1110;
endmodule

```

para ejecutarlo:
En el top (o constraints `.xdc`), conectamos los pines de la forma:
- `seg[6:0]` → `CA` a `CG`
- `an[3:0]` → `AN3` a `AN0`

y ejecutamos:
```verilog
top_display_un_numero mostrar(
    .num(4'hB),
    .seg(seg),
    .an(an)
);
```
