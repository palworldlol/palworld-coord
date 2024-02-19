# Palworld Coordinate Converter

* *Developed by https://palworld.lol with major help from  https://github.com/cmkb3*
* *[A blog post covering](https://blog.palworld.lol/reverse-engineering-palworld-coordinate-system/) some of the reason behind this library*

# What is this?

This is a small library with two functions used to convert between two different coordinat systems in Palworld:

1. The coordinate system used in the game itself in the Paldex interactive map
2. The coordinate system used in the game save files (`.sav`)

## Installation

```shell
pip install palworld-coord
```

Also, if you want, you can just copy the [contents of this file](src/palworld_coord/__init__.py) into your project instead of adding a dependency. 

## API

```python
# Convert from save game file coordinate to Paldex
sav_to_map(x: float, y: float) -> Point
# Convert from Paldex coordinate to save game file
map_to_sav(x: int,   y: int) -> Point
```

## Usage Examples


```python
from palworld_coord import sav_to_map, map_to_sav

# Anubis boss location pulled from game data
sav_to_map(-167230, 96430)
# Point(x=-134, y=-94)

# Get .sav coordinates of random base location in-game:
map_to_sav(373, -359)
# Point(x=-288669, y=329207)
```
