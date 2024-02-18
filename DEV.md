# Development Docs
There are some magic numbers used in this library. Here is where they come from...

*NOTE*: I'm not experienced with documenting maths so if anyone has some feedback, please open a GitHub Issue.

## TL;DR

The translation/shift magic numbers come from the midpoint of the min/max positions in coordinate system in .sav files: $(−123888, 158000)$.

The scaling number $459$ comes from ratio of distance between min/max points in .sav file vs Paldex map.

## Min and Max coordinates
The minimum and maximum points (bottom-left and top-right) of Palworld are below. This is using the coordinate system stored in the .sav files:

$$
(-582888.0, -301000.0)\\
( 335112.0,  617000.0)
$$

These values were pulled from `DT_WorldMapUIData.json` (TODO needs source).

The in-game Paldex map goes from:

$$
(-1000, -1000)\\
( 1000,  1000)
$$


## Midpoints
Find the midpoints of each coordinate system to see how they align. For the in-game Paldex one, its obvious without 
doing any thing the midpoint is $(0,0)$. For the coordinate system used in the .sav files:

$$
(X₁ + X₂) / 2, (Y₁ + Y₂) / 2 \\
(-582888 + 335112) / 2, (-301000 + 617000)/2 \\
(−123888, 158000)
$$

We can use these numbers to tranlate/shift from .sav coordinates to Paldex coodinates since they have different origins.


## Distance
Find the distance between min/max points for each coordinate system so we can scale accordingly. 

Max/min distance in .sav files:
$$
D_{1} = \sqrt((x2 – x1) + (y2 – y1)²) \\
D_{1} = \sqrt((-582888 – 335112)² + (-301000 – 617000)²) \\
D_{1} = 1298248.050258501
$$

Max/min distance in Paldex map:
$$
D_{2} = \sqrt((x2 – x1)² + (y2 – y1)²) \\
D_{2} = \sqrt((-1000 – 1000)² + (-1000 – 1000)²) \\
D_{2} = 2828.427124746
$$

And finally, we can get the number we will use to scale coordinates:
$$
D_{1} / D_{2} \\
1298248.050258501 / 2828.427124746 \\
459
$$