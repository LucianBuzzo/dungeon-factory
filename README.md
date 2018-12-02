<div align="center">
  <img width="200" height="200" src="https://raw.githubusercontent.com/LucianBuzzo/dungeoneer/master/architecture-blueprint-svgrepo-com.png">
  <br>
  <br>

[![Build Status](https://travis-ci.org/LucianBuzzo/dungeoneer.svg?branch=master)](https://travis-ci.org/LucianBuzzo/dungeoneer)
[![npm version](https://badge.fury.io/js/dungeoneer.svg)](http://badge.fury.io/js/dungeoneer)
[![Dependency Status](https://img.shields.io/david/LucianBuzzo/dungeoneer.svg)](https://david-dm.org/LucianBuzzo/dungeoneer)

  <h1>Dungeoneer</h1>

  <p>
    Procedurally generate beautiful 2d dungeons for your game.
    <br>
    https://lucianbuzzo.github.io/dungeoneer
  </p>
  <br>
  <br>
</div>

This module is a tool for generating random dungeons as a two dimensional array.
It is largely based on the excellent work of [Bob
Nystrom](https://github.com/munificent) and his game
[Hauberk](http://munificent.github.io/hauberk/), which you can read about [here](http://journal.stuffwithstuff.com/2014/12/21/rooms-and-mazes/).

A demo of this module can be seen here https://lucianbuzzo.github.io/dungeoneer/

## Installation

Install `dungeoneer` by running:

```sh
$ npm install --save dungeoneer
```

## Usage

```js
const dungeoneer = require('dungeoneer')

const dungeon = dungeoneer.build({
  width: 21,
  height: 21
})
```

The `build` method will return a dungeon object. The shape of the dungeon
object is defined below:

```ts
type Tile = {
  // An object containing the tiles immediately surrounding this tile.
  nesw: {
    n?: Tile;
    ne?: Tile;
    e?: Tile;
    se?: Tile;
    s?: Tile;
    sw?: Tile;
    w?: Tile;
    nw?: Tile;
  };

  // 'floor' and 'door' are passable terrain and a wall is impassable terrain.
  type: 'wall' | 'floor' | 'door';
}

type Room = {
  height: number;
  width: number;
  x: number;
  y: number;
}

type Dungeon = {
  rooms: Room[];
  tiles: Array<Tile[]>;
}
```

## License

The project is licensed under the MIT license.

The icon at the top of this file is provided by
[svgrepo.com](https://www.svgrepo.com/svg/293783/architecture-blueprint) and is
licensed under [Creative Commons BY
4.0](https://creativecommons.org/licenses/by/4.0/).
