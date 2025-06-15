
# Edges restructure project: Refactor HexaRealm/Edges/ to be modder friendly

The file structure for Edges/ in HexaRealm are a bit whimsical, and wildcard Land terrain used - it makes edge modding hell, unless a modder creates a stand-alone TileSet mod, which can very well be out of their mods' scope...

The edge file/dir structures are baked into Unciv, so any mod alterations must clone or compete with the existing files in pre-existing structure. Not _too_ big of a deal, except... it just gets messy the deeper you get into modding edges.

This mod serves only to demonstrate HexaRealm as rebuilt with mod-friendly assets for PR submission as proof of work. After the PR is dealt with however that turns out this mod is obsolete.


# Structural updates

- Dirs are all presumed under Images/TileSets/EdgeRealm/Edges/ (submitted as HexaRealm/Edges)
- No modifications to jsons/TileSets/HexaRealm.json only copied to EdgeRealm.json
- How to name dirs? "base terrain" is a matter of perspective, so title-terrain1/ will not include converse title-terrain2-terrain1 assets, thus properly residing in title-terrain2/
- `maps/Wonder edge test` included for quick review

## New structure

```
Edges/[title]-[terrain1]/
Edges/[title]-[terrain1]/[title]-[terrain1]-[terrain2]-[side].png
```

## Change notes

1. Coast-Land Art/ removed, no Land terrain wildcarding
2. Assets relocated per existing edge terrain
3. Dirs like "Desert+Mountain-Coast Art/" relocated to each respective dir
4. No new assets nor renamed assets, original titles retained
5. Water-oriented wonders uses `turnsInto` to detemine what terrain is edged, no action required


# Other notes

## More-edges
- Mod [More-Edges](https://github.com/hackedpassword/More-edges) will need structure updating for compatibility
- Doesn't work atm w/ EdgeRealm enabled, prob due to competing file dates

## Some edge design notes for modders

Follow the bouncing ball: the 2nd element, named as the first terrain, is the base terrain the edge will be applied to at the named [side] **inner edge**.

[title]-[base_terrain]-[adjacent_terrain]-[side].png == (element 1)-(element 2)-(element 3)-(element 4).png

The 3rd element, named as the 2nd terrain, is the expected adjacent terrain where this edge will activate. To design edges that work on the outside, you build the outside edges and apply them inversely inside the hex. Simple to describe, a pain to detail.
