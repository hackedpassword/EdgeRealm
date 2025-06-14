
# Edges restructure project

Purpose: Refactor HexaRealm/Edges/ to be modder friendly.

Modding edges as an enhancement mod of HexaRealm is a double-edged sword - the file/dir structures are baked into Unciv, so any mod alterations must clone the existing files in pre-existing structure. Not too big of a deal, except...

Adding custom edges for Coast-Land are effectively impossible, due to the Land wildcard quashing more specific terrains like Wonders (per my experience). Meaning Coast-Land is the catch-all edge regardless of mod edges for new edges.

This mod serves only to demonstrate HexaRealm rebuilt with mod-friendly assets, for those looking to mod their edges without a full blown TileSet mod.

## Design note for sanity

Follow the bouncing ball: the 2nd element, named as the first terrain, is the base terrain the edge will be applied to at the named [side] **inner edge**.

[title]-[base_terrain]-[adjacent_terrain]-[side].png == (element 1)-(element 2)-(element 3)-(element 4).png

The 3rd element, named as the 2nd terrain, is the expected adjacent terrain where this edge will activate. To design edges that work on the outside, you build the outside edges and apply them inversely to the hex. Simple to describe, a pain to detail.

# Changes documented

- Dirs are all presumed under Images/TileSets/HexaRealm/Edges/
- No modifications to jsons/TileSets/HexaRealm.json
- Atlas regen will alias redundant image assets as usual
- More dirs created vs more files per dir for structural clarity
- Mod [More-Edges](https://github.com/hackedpassword/More-edges) will need structure updating to reflect these changes
- How to name dirs? "base terrain" is a matter of perspective, so title-terrain1/ will not include converse title-terrain2-terrain1 assets, thus properly residing in title-terrain2/

## New structure

```
Edges/[title]-[terrain1]/
Edges/[title]-[terrain1]/[title]-[terrain1]-[terrain2]-[side].png
```

## Change notes

1. Coast-Land Art/ removed. Assets moved to Beach-Coast/, replicated per terrain and renamed as Beach-Coast-[terrain]-[side].png
2. Dirs with merged terrains, i.e. "Desert+Mountain-Coast Art/" reset to each respective dir
3. Assets not originally appearing in first-gen edges, but created in More-edges mod, remain exclusive
4. No new assets nor renamed assets, original titles retained
