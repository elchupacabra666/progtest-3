# Hodiny na věži

### Termín odevzdání: 14.11.2022 11:59:59  
### Max. hodnocení: 5.000 (bez bonusů)  

## Zadání

Úkolem je vytvořit funkci, která vypočítá, kolikrát budou zvonit zvony na věži v zadaném časovém intervalu.

### Zadání funkcionality:

Hodiny na věži mají dva zvony:
- **Zvon #1** odbíjí minuty. Odbíjí v násobcích 15 minut:
  - XX:00 - 4x
  - XX:15 - 1x
  - XX:30 - 2x
  - XX:45 - 3x
- **Zvon #2** odbíjí hodiny, zvoní tolikrát, kolik ukazuje hodinová ručička:
  - 12x ve 12:00 a půlnoci, 1x v 1:00, 2x ve 2:00, atd.
  
- **Odbíjení je vypnuto v neděli**. Zvoní naposledy v sobotu ve 23:45 a znovu až v pondělí v 00:00.

### Funkce má rozhraní:

```cpp
int bells ( int y1, int m1, int d1, int h1, int i1,
            int y2, int m2, int d2, int h2, int i2, 
            long long int * b1, long long int * b2 );
```

- **y1, m1, d1, h1, i1** - rok, měsíc, den, hodina a minuta počátku intervalu
- **y2, m2, d2, h2, i2** - rok, měsíc, den, hodina a minuta konce intervalu
- **b1** - počet odbití zvonu #1 (minuty)
- **b2** - počet odbití zvonu #2 (hodiny)

### Požadavky na implementaci:

1. Funkce vrací:
   - `1` při úspěchu (platné vstupní parametry),
   - `0` při neúspěchu (neplatné vstupy, např. nesprávný interval).
  
2. Podmínky pro validní vstupy:
   - Rok ≥ 1600.
   - Platné hodnoty měsíců (1-12), dní (1-počet dní v měsíci), hodin (0-23), minut (0-59).
   - Počáteční čas musí být dříve než koncový čas.

### Specifikace:

- **Gregoriánský kalendář**:
  - Nepřestupné roky (kromě let dělitelných 4, ale ne 100, s výjimkou dělitelných 400).
  
### Nápovědy:

- Pro lepší práci s časem převést hodnoty na jinou reprezentaci (např. počítání minut od určitého data).
- Pro velké intervaly je nutné použít efektivnější algoritmus (např. předpočítat odbíjení za jeden den).

### Ukázka základních testů:

```cpp
bells( 2000, 12, 26, 0, 0, 2000, 12, 31, 0, 0, &b1, &b2 );
// return 1, b1 = 1200, b2 = 780

bells( 2000, 12, 27, 0, 0, 2000, 12, 27, 0, 0, &b1, &b2 );
// return 1, b1 = 4, b2 = 12

bells( 1932, 4, 8, 21, 50, 1980, 2, 26, 1, 22, &b1, &b2 );
// return 1, b1 = 3597635, b2 = 2338474

bells( 1954, 9, 13, 19, 30, 2012, 11, 11, 21, 6, &b1, &b2 );
// return 1, b1 = 4370205, b2 = 2840642
```

### Důležité poznámky:

- Program pracuje v omezeném testovacím prostředí s omezenou pamětí a časem běhu.
- Základní naivní řešení prochází všechny odbíjení, ale pro velké intervaly je potřeba efektivnější algoritmus.

