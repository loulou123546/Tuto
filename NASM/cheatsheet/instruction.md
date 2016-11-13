# instructions

```
model:
name $1, $2 ; explication
```


| abrev | explication |
| :------: | :------: |
| r | registre (ah , bx, ...) |
| a | addresse dans RAM (ettiquette) |
| v | valeur dans RAM ( [ettiquette] ) |
| i | valeur immédiate (15, 0x4E) |
| 8 | doit être sur 8 bits (ah, al) |
| X | doit être sur le même nb de bits |

---

```
mov r/v-X, r/a/v/i-X    ; copie $2 dans $1

ret                     ; arrete le programme

int i                   ; appel l'interruption $1

inc $1                  ; incrémente $1
dec $1                  ; décrémente $1

add $1, $2              ; $1 = $1 + $2
sub $1, $2              ;
```