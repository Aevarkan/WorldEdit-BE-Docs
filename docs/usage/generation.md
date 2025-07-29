# Generation

WorldEdit comes with a few commands help you make shapes without the use of a region selection. Instead, it takes the block that you are standing in as the center of these shapes.

To understand the command syntaxes, check the [Commands](../commands.md) page.

[TOC]

## Spheres and Domes

```txt
;sphere [-hr] <pattern> <radius> [radiusY] [radiusZ] [-d <dome>]
;hsphere [-r] <pattern> <radius> [radiusY] [radiusZ] [-d <dome>]
```

This generates a sphere or spheroid of any dimensions. You can also define 2, or 3 numbers to define the radius in different axes. `-h` makes it hollow, and `-r` raises the sphere's bottom to the origin. By adding the `-d` flag along with a direction, you can turn the sphere into a dome. For example, `;sphere -d up stone 10` creates a top half dome of stone.

## Cylinders

```txt
;cyl [-hr] <pattern> <radius> ([radiusY]) [height] [-d <direction>]
;hcyl [-r] <pattern> <radius> ([radiusY]) [height] [-d <direction>]
```

This generates a cylinder of any dimensions. You can also define 2 numbers to define the radius in different axes. Again, `-h` makes it hollow, and `-r` raises the its bottom to the origin. To change the direction the cylinder generates in, add the `-d` flag along with a direction. For example, `;cylinder -d north stone 4 10` creates a stone cylinder pointing north.

## Pyramids

```txt
;pyramid [-h] <pattern> <size>
;hpyramid <pattern> <size>
```

This generates a pyramid. Unlike the previous two shapes, the center is at the base of the pyramid.

## Toruses

```txt
;torus [-h] <pattern> <outerRadius> <innerRadius> [-d <direction>]
```

This generates a torus with varying inner radius and outer radius. Outer radius is how big the torus is, and the inner radius is how thick it is. `-r` and `-d` behave the same way as in [Cylinders](generation.md#cylinders). Whether the torus generates from its bottom, and the direction it generates in.

## Lofts

```txt
;loft start
;loft set <pattern>
;loft remove
;loft clear
```

Lofts are a group of segments that form a shape. These can be used to make things like flags and ramps. Because of how complex they are, there are four subcommands to manage their creation.

`;loft start` puts you into loft mode. You're usual ways of making selections (`;pos`, `;hpos` commands and selection wands) will be used to create the segments that make up the loft. While in loft mode, the first selection mark is used to create a new segment in the loft, with the marked position as its first point; the second selection mark grows the segment by adding more points to it.

Once you have all your segments, use `;loft set <pattern>` to fill it in with your pattern of choice. For example, `;loft set wool`. If you want to remove points from your selection, use `;loft remove` To remove the last point added. And when you're ready to leave loft mode, use `;loft clear`.

## Custom Shapes

Apart from these builtin shapes, there's also the ability to make your own with the `;gen` command!

```txt
;gen [-h] <pattern> <expression>
```

Unlike the others, you need to first make a selection to define where the shape will be made. Then, you need to define an expression that will determine where blocks will be generated. If it returns true or a number besides 0, then a block is generated. You can use the three variables `x`, `y` and `z` to reference the location, which is normalized within the selection ([-1, -1, -1] - [1, 1, 1]). You also have a bunch of math functions at your disposal. Experiment!

!!! Examples

    `;gen -h stone "y < x^2-z^2"`- Generates a stone saddle

    `;gen stone "(0.75-sqrt(x^2+y^2))^2+z^2 < 0.25^2"` - Generates a stone torus

    `;gen glass "y < cos(sqrt(x^2+z^2)^2 * 10) * 0.2"` - Generates a radial cosine wave

    `;gen -h wool "y^2/9+x^2/6*(1/(1-0.4*y))+z^2/6*(1/(1-0.4*y))<0.08"` - Generates a hollow wooly egg
