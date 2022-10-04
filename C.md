# Language C
```C
#include <stdio.h>
/*
Ce programme affiche un message
*/
int main (void){
  printf ("Bienvenue dans ce cours du langage C! \n");
  return(0);
} 
```

# Entrées/sorties printf et scanf
- `c` : Character.
- `s` : String of characters

- `d` or `i` : signed decimal integer
- `u` : Unsigned decimal integer
- `f` : Decimal floating point
- `ld` : long
- `lu` : unsigned long 
- `hu` : Unsigned short int integer

- `e` : notation scientifique avec un 'e' minuscule
- `E` : notation scientifique avec un 'E' majuscule
- `g` : Uses the shorter of %e or %f
- `G` : Uses the shorter of %E or %f

- `o` : Signed octal
- `x` : Unsigned hexadecimal integer
- `X` : Unsigned hexadecimal integer (capital letters)
- `p` : Pointer address
- `n` : Nothing printed
- `%` : Character

- `f` : float
- `lf` : longfloat, double
- `s` : chaine de caractere -> char
- `u` : unsigned int, unsigned short

# Les variables
Un identificateur de variable ne doit pas commencer par un chiffre.
### Différents types :
- char (1 octets)
- int (2 octets)
- short (2 ou 4 octets)
- long (4 octets)
- float (4 octets)
- double (8 octets)
chacun peut être signed ou unsigned.

Pour exprimer une donnée en octal on utilise 0 -> 0125
Pour exprimer une donnée en hexadécimale on utilise 0x -> 0x12

## Déclarer des constantes
#define nom de la constante valeur
