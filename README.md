# xlisting
Provides Cross Referenced Listing and Source Variables at Console


Installation using SWI-Prolog 7.1 or later:

    `?- pack_install(rtrace).`

  or

    `?- pack_install('https://github.com/logicmoo/rtrace.git'). `

This module uses [semantic versioning](http://semver.org/).

Source code available and pull requests accepted at
http://github.com/logicmoo/rtrace

```prolog

?- use_module(library(rtrace)).
true.

?- rtrace(member(X,[1,2,3])).
   Call: (9) lists:member(_8730, [1, 2, 3])
   Unify: (9) lists:member(_8730, [1, 2, 3])
   Exit: (9) lists:member(1, [1, 2, 3])
X = 1 ;
   Redo: (9) lists:member(_8730, [1, 2, 3])
   Exit: (9) lists:member(2, [1, 2, 3])
X = 2 ;
   Redo: (9) lists:member(_8730, [1, 2, 3])
   Exit: (9) lists:member(3, [1, 2, 3])
X = 3.

?-  rtrace(member(X,[1,2,3])),member(Y,[4,5]).
   Call: (10) lists:member(_10508, [1, 2, 3])
   Unify: (10) lists:member(_10508, [1, 2, 3])
   Exit: (10) lists:member(1, [1, 2, 3])
X = 1,
Y = 4 ;
X = 1,
Y = 5 ;
   Redo: (10) lists:member(_10508, [1, 2, 3])
   Exit: (10) lists:member(2, [1, 2, 3])
X = 2,
Y = 4 ;
X = 2,
Y = 5 ;
   Redo: (10) lists:member(_10508, [1, 2, 3])
   Exit: (10) lists:member(3, [1, 2, 3])
X = 3,
Y = 4 ;
X = 3,
Y = 5.

?- rtrace((member(X,[1,2,3]),member(Y,[4,5]))).
   Call: (10) lists:member(_11854, [1, 2, 3])
   Unify: (10) lists:member(_11854, [1, 2, 3])
   Exit: (10) lists:member(1, [1, 2, 3])
   Call: (10) lists:member(_11872, [4, 5])
   Unify: (10) lists:member(_11872, [4, 5])
   Exit: (10) lists:member(4, [4, 5])
X = 1,
Y = 4 ;
   Redo: (10) lists:member(_11872, [4, 5])
   Exit: (10) lists:member(5, [4, 5])
X = 1,
Y = 5 ;
   Redo: (10) lists:member(_11854, [1, 2, 3])
   Exit: (10) lists:member(2, [1, 2, 3])
   Call: (10) lists:member(_11872, [4, 5])
   Unify: (10) lists:member(_11872, [4, 5])
   Exit: (10) lists:member(4, [4, 5])
X = 2,
Y = 4 ;
   Redo: (10) lists:member(_11872, [4, 5])
   Exit: (10) lists:member(5, [4, 5])
X = 2,
Y = 5 ;
   Redo: (10) lists:member(_11854, [1, 2, 3])
   Exit: (10) lists:member(3, [1, 2, 3])
   Call: (10) lists:member(_11872, [4, 5])
   Unify: (10) lists:member(_11872, [4, 5])
   Exit: (10) lists:member(4, [4, 5])
X = 3,
Y = 4 ;
   Redo: (10) lists:member(_11872, [4, 5])
   Exit: (10) lists:member(5, [4, 5])
X = 3,
Y = 5.

```

[BSD 2-Clause License](LICENSE.md)

Copyright (c) 2017, 
Douglas Miles <logicmoo@gmail.com>
All rights reserved.

