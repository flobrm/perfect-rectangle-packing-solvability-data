# Perfect rectangle packing puzzles
This repository contains a set of 7200 puzzles for perfect rectangle packing categorized by the number of tiles (n) and the maximum possible tile size (t_max). 


## Dataset description
For each combination of n and tmax a set of 100 unique puzzles was generated by sampling a set of allowed tiles (all non-square tiles with sides <= t_max) and searching for a frame with the same area as the combined tiles. 
The resulting puzzles have a number of guarantees:
* The total area of the frame is equal to the total area of the selected tiles.
* The frame is large enough that each tile fits horizontally and vertically.
* Each tile in a puzzle is unique, no two tiles in a puzzle will have the same dimensions.
* There are no square tiles in the allowed tileset.

Note that it's not required for the largest tiles in a puzzle to actually have a side of length t_max. There are for example puzzles in group of puzzles with 18 tiles and t_max 20 where the actual largest tile side is only 19 instead of 20.

Additionally there are not enough valid tileset permutations to create 100 puzzles for a large n and a small t_max. The table below shows the ranges of puzzles included in the dataset.

|Tiles (n)|Max possible tile length (t_max)|Number of puzzles|
|---|---|---|
|6-12|6-30|2500
|13-19|7-30|2400
|20|8-30|2300

## Formatting format
These puzzles are available in csv format with the following fields:
* id: An arbitrary reference number
* tmax: The maximum tile size according to the generator. All tile sides in the puzzle will be  <= tmax
* num_tiles: The number of tiles in the puzzle
* frame_width and frame_height: The dimensions of the frame tiles have to be placed in.
* tiles: A json encoded array of tile objects with a width ('X') and height('Y').  For each tile X > Y 
* has_solutions:  The solvability of this puzzle. 1 If a solution exists for this puzzle, 0 otherwise.
* recursions: How many tiles we placed (and possibly removed again) to determine the puzzle's solvability. This could be a rough indication of difficulty.
