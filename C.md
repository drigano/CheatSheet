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

# Les printf
- `c` : Character.
- `d` or `i` : signed decimal integer
- `e` : notation scientifique avec un 'e' minuscule
- `E` : notation scientifique avec un 'E' majuscule
- `f` : Decimal floating point
- `g` : Uses the shorter of %e or %f
- `G` : Uses the shorter of %E or %f
- `o` : Signed octal
- `s` : String of characters
- `u` : Unsigned decimal integer
- `hu` : Unsigned short int integer
- `x` : Unsigned hexadecimal integer
- `X` : Unsigned hexadecimal integer (capital letters)
- `p` : Pointer address
- `n` : Nothing printed
- `%` : Character

# Les scanf
- `c` : char
- `d` : int, short
- `ld` : long
- `f` : float
- `lf` : longfloat, double
- `s` : chaine de caractere -> char
- `u` : unsigned int, unsigned short
- `ul` : unsigned long

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
