# assembleur-tuto
tuto sur l'assembleur (nasm)


### les registres

```
|---------------------------------------|
|    Ax   |    Bx   |    Cx   |    Dx   |
| Al | Ah | Bl | Bh | Cl | Ch | Dl | Dh |
|----|----|----|----|----|----|----|----|
|    |    |    |    |    |    |    |    |
| FF |    |    |    |    |    |    |    |   mov al,0xFF
| FF | FE |    |    |    |    |    |    |   mov ah,254
| FF | FE | 18 | 13 |    |    |    |    |   mov bx,0x1318 ; premier => haut
|    |    |    |    |    |    |    |    |
|    |    |    |    |    |    |    |    |
|    |    |    |    |    |    |    |    |
|    |    |    |    |    |    |    |    |
|    |    |    |    |    |    |    |    |
|    |    |    |    |    |    |    |    |
|    |    |    |    |    |    |    |    |
|    |    |    |    |    |    |    |    |
|    |    |    |    |    |    |    |    |
|    |    |    |    |    |    |    |    |
```


### les adresses (RAM)

```
|---------|---------|
| adresse | contenu |
|---------|---------|
|   ...   |   ...   |
|   0x48  |  0x54   |
|   ...   |   ...   |
|   0x54  |  0x8F   |
|   ...   |   ...   |
```

```NASM
mov ah, hexatruc    ; ah = 0x48  soit l'addresse de hexatruc
mov al, [hexatruc]  ; al = 0x54  soit la valeur de hexatruc

ret

hexatruc: db 0x54
```


### Arithmétique

```NASM
; $1 et $2 doivent etre de même taille !!!

add $1, $2    ; $1 = $1 + $2
sub $1, $2    ; $1 = $1 - $2
mul $1, $2    ; $1 = $1 * $2
; pour DIV voir ci-dessous


; autre méthode connu

mul $1        ; Ah = Al * $1          $1 doit etre sur 1 octet
mul $1        ; Dx:Ax = Ax * $1       $1 doit etre sur 2 octet
mul $1,$2,$3  ; $1 = $2 * $3          $1, $2 et $3 de même taille

div $1        ; divise Ax par $1       Quotient dans Al   Reste dans Ah        $1 en 1 octet
div $1        ; divise Dx:Ax par $1    Quotient dans Ax   Reste dans Dx        $1 en 2 octet
```

### porte logique


```
|---|---|---|
| 0 | 0 | A |
| 1 | 0 | B |
| 0 | 1 | C |
| 1 | 1 | D |
|---|---|---|
```
```NASM
and $1, $2   ; $1 = 1 pour D
or $1, $2    ; $1 = 1 pour BCD
xor $1, $2   ; $1 = 1 pour BC

not $1       ; inverse $1 et le retourne dans $1
```
toutes les porte logique change le drapeau `ZF` à `1` si le resultat est null, à `0` sinon.
