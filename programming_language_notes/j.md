# [J][jsoftware]
## General
### Apply function to subarrays
```j
f =: -/&> NB. Subtract values in subarrays

X =: 1 2 ; 3 4 ; 5 6
f X NB. => _1 _1 _1
```

### Conversion Examples
#### Type (`3!:0`)
See <https://www.jsoftware.com/help/dictionary/dx003.htm>.

```j
3!:0 'w00t'    NB. => 2 (literal)
3!:0 (3)       NB. => 4 (integer)
3!:0 (3.5)     NB. => 8 (floating point)
```

#### To Literal (`":`)
```j
3!:0 (77.89)        NB. => 8 (floating point)
3!:0 (": 77.89)     NB. => 2 (literal)
3!:0 (": 77 8 9)    NB. => 2 (literal)

w =: 'w00t--'
w , 77          NB. => domain error
w ,": 77        NB. => w00t--77
w ,": 77.89     NB. => w00t--77.89
w ,": 77 8 9    NB. => w00t--77 8 9
<w ,": 77 8 9   NB. => ┌────────────┐
                       │w00t--77 8 9│
                       └────────────┘
```

### Slice
```j
u =: 1 + i.10 NB. => 1 2 3 4 5 6 7 8 9 10

NB. Take index 7 (Take 1 starting with index 7)
1 {. 7 }. u NB. => 8

NB. Take 3 starting with index 2
3 {. 2 }. u NB. => 3 4 5
```

### Take Value(s) at Random Index from Array
```j
values =: 'ABCDEFGHIJKL'

take_random_index =: 3 : 0
  (1 ? #y) { y
)

take_random_index values NB. => [A-L]

take_random_value =: 3 : 0
  take_random_index values
)

take_random_value 9909123 NB. => [A-L]
take_random_value &> i.1 NB. => [A-L] ;
take_random_value &> i.5 NB. => [A-L] ; [A-L] ; [A-L] ; [A-L] ; [A-L]

take_random_values =: 3 : 0
  vals =: take_random_value &> i.y
  (1 , #vals) ($ ,) vals
)

take_random_values 10 NB. => [A-L] [A-L] [A-L] [A-L] [A-L] [A-L] [A-L] [A-L] [A-L] [A-L]
```

### [Plot][plot]
```j
load 'plot'

NB. Hill's Prescription Diet
NB. c/d Multicare with Chicken
NB. Dry Cat Food
NB. https://www.hillspet.com/cat-food/pd-cd-multicare-feline-with-chicken-dry
NB. accessed 11.01.2021

NB. Adult Maintenance
NB. cat mass in kilograms
X =: 2.7 3.6 4.5 5.4 6.4 7.3 8.2

NB. grams of food per day
Y =: 45 55 70 80 90 100 100

plot_cat_reg =: 4 : 0
  b =. y %. 1 ,. x
  xlbl=. 'Cat Mass (kg)'
  ylbl=. 'g Food/Day'
  tittxt=. 'Cat Mass Regression'
  keytxt=. 'Rec.,Est.'
  pd 'reset'
  pd 'title ',tittxt
  pd 'xcaption ',xlbl
  pd 'ycaption ',ylbl
  pd 'key ',keytxt
  pd 'keystyle marker'
  pd 'keycolor gray'
  pd 'itemcolor gray'
  pd 'keymarkers circle,line'
  pd 'type marker'
  pd 'markers circle'
  pd x;y
  pd 'type line'
  pd x;b p. x
  pd 'show'
)
```

### [Valence][valence]: Monadic, Dyadic, and Ambivalent functions
```j
u =: 1 + i.5
v =: 10 + u

NB. =============================================
NB. Square root
m =: 3 : 0 
  %: y
) NB. strictly monadic

m u NB. => 1 1.41421 1.73205 2 2.23607
m v NB. => 3.31662 3.4641 3.60555 3.74166 3.87298

NB. =============================================
NB. n-root
d =: 4 : 0
  x %: y
) NB. strictly dyadic

u d v NB. => 11 3.4641 2.35133 1.93434 1.71877
v d u NB. => 1 1.05946 1.08818 1.10409 1.11326

NB. =============================================
NB. Negate monadic, divide dyadic
a =: - : % NB. ambivalent

a u NB. => _1 _2 _3 _4 _5
a v NB. => _11 _12 _13 _14 _15

u a v NB. => 0.0909091 0.166667 0.230769 0.285714 0.333333
v a u NB. => 11 6 4.33333 3.5 3
```

## License
<a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-nc/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/">Creative Commons Attribution-NonCommercial 4.0 International License</a>.

[jddb]: https://code.jsoftware.com/wiki/Jd/Index
[jsoftware]: https://www.jsoftware.com/
[plot]: https://code.jsoftware.com/wiki/Plot
[valence]: https://code.jsoftware.com/wiki/Vocabulary/Valence
