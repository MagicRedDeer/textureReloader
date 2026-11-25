> Mirror of [iceanimations/textureReloader](https://github.com/iceanimations/textureReloader), published
> by the studio under EPL 2.0. Kept here for reference; the original repository is the canonical one.

# textureReloader

Finds every file the renderer actually reads, shows it, and lets an artist repoint or reload it without
hunting through the hypershade.

A Maya scene's textures are spread across node types that all mean "this image" in different ways: plain
`file` nodes, Redshift normal maps, dome lights, IES profiles, sprites. A path that broke at the filesystem
level breaks all of them, and the artist only sees it when the render comes back grey. This tool
enumerates them by type, groups them, and remaps or reloads in bulk.

## What it does

- `src/backend.py` collects texture-bearing nodes by exact type: `RedshiftNormalMap`,
  `RedshiftDomeLight`, `RedshiftIESLight`, `RedshiftSprite`, and ordinary `file` nodes, wrapped in small
  classes that expose the path attribute uniformly.
- `src/remap.py` is the interface: list, preview, remap to a new root, reload.
- `src/window.py` handles the Qt window and the Maya window parenting.

It is a Redshift-era tool, which is why the node types are spelled out rather than discovered.

## Authorship

23 commits between 2013 and 2021:

| Author | Commits |
|---|---|
| Qurban Ali | 14 |
| Talha Ahmed | 6 |
| unattributed | 3 |

Qurban Ali wrote most of this one on my team. Mirrored as part of the toolbox, not as an example of my
code.

LICENSE
=======

Copyright 2021. Talha Ahmed. All rights reserved.

This work is licensed under the terms of Eclipse Public License - v 2.0.
For a copy see https://www.eclipse.org/org/documents/epl-2.0/EPL-2.0.txt
