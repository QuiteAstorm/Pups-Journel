# Behind the Puppy Paws — The Paint Bucket That Thought It Was a Crayon 🐾

**Project:** My Happy Pups Coloring Studio  
**Status:** Coding lesson and testing notes; PR #40's shading-aware changes still need owner testing.

## The observation that started it

While testing Tap to Fill on Butterscotch's black-and-white glasses portrait, the owner noticed that color filled unevenly and looked like crayon marks. She reasoned that the many pencil strokes and shaded lines used to make Butterscotch recognizable were interfering with the tool's ability to fill a whole space.

That observation was the important clue. You don't have to know a technical term to identify a software problem.

## What was happening?

The puppy-house sample uses simple, predefined SVG shapes, so Tap to Fill knows which shape was tapped. Imported pictures are raster images made of pixels, not predefined shapes. The first imported-image paint bucket used **flood fill**: starting at a tapped pixel, it checks neighboring pixels and spreads color through those that meet its rules. Pencil shading sometimes failed those rules and was mistaken for an edge, leaving patchy unfilled areas.

## New coding concepts

- **Algorithm:** A repeatable set of steps a computer follows to solve a problem.
- **Flood fill:** Finds a connected region by examining neighboring pixels, like the paint-bucket tool.
- **Pixel:** One tiny point of color in a digital image.
- **Brightness (luminance):** A numerical estimate of how light or dark a pixel is.
- **Tolerance / threshold:** Controls which pixels are similar enough to be included, and which are treated as barriers.
- **Boundary detection:** Distinguishes an area's edge from marks inside the area.
- **Neighborhood averaging:** Looks at nearby pixels together to reduce the effect of isolated shading strokes.
- **Opacity / alpha:** Controls how strongly new color covers existing artwork; using less opacity over dark lines can help retain facial details.
- **HTML Canvas and JavaScript:** Browser features used to inspect image pixels and paint the results.

## What we changed (proposed PR #40)

Added a **Shading Tolerance** slider, used neighborhood-averaged brightness to decide where color can spread, and varied the color's opacity to help preserve dark pencil details. Each fill remembers its tolerance for undo/redo and saved versions. The original SVG house fill and brushes were left alone.

**Important:** This is a heuristic, not magical recognition of Butterscotch. Higher tolerance can accidentally cross thin outlines, while lower tolerance may still leave patches. Test on the actual coloring page, use Undo, and adjust the slider. A photo may not fill well.

## Why this wasn't obvious from CSS classes

CSS styles a page. Bootstrap provides prebuilt UI styles and components. Sass helps author CSS. None of them automatically solves image segmentation. For that we needed JavaScript, pixel processing, and an algorithm.

## Beginner developer takeaway

1. Observe what actually happens.
2. Describe the result in everyday words.
3. Find out what kind of problem it is.
4. Learn the terms that make research easier.
5. Make a small change, test it, and adjust without breaking working features.

**Journal lesson:** You can recognize a real programming problem long before you know the algorithm that might solve it. The user's observation about Butterscotch's shading led directly to the next experiment.

**Privacy:** Personal family portraits are not included in this public repository; this note describes the technique only.
