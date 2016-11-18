# Loyd-s-Puzzle
Modeling Loyd's Puzzle (3x3) using NuSMV

Loyd's puzzle has an NxK grid with N.K - 1 numbered tiles and a blank tile. There are two arrays, h and v, that keep track of the horizontal and vertical positions of the tiles respectively, such that the position of tile i is given by h[i] and v[i]. Tile 0 represents the blank tile. Position h[i] = 1 and v[i] = 1 is the lowest left corner of the puzzle. Here, we define the action move [actions up, down, left and right] with reference to Tile 0. For example, if Tile 1 is to the left of Tile 0, the move left results in Tile 0 moving left and Tile 1 moving
right. The initialization of all the tiles is done according to the given initial configuration. The next position of each tile is depended on move of Tile 0. Next position of Tile 0 is defined as follows.

a. If the action move is up and Tile 0 is not in the last row, then move up (h[0] + 1)
b. If the action move is down and Tile 0 is not in the fist row, then move down (h[0] - 1)
c. If the action move is left and Tile 0 is not in the first column, then move left (v[0] - 1)
d. If the action move is right and Tile 0 is not in the last column, then move right (v[0] + 1)
e. Otherwise, remain in the same position.

Next position of Tile i (1-8) is defined as follows.

a. If the action move is down, Tile 0 is not in the first row, the vertical positions of Tile 0 and Tile i are equal and Tile i is below Tile 0 (h[i] = h[0] - 1), OR, if the action move is down, Tile 0 is not in the last row, the vertical positions of Tile 0 and Tile i are equal and Tile i is above Tile 0 (h[i] = h[0] + 1), then horizontal position of Tile i is equal to that of Tile 0.

b. If the action move is right, Tile 0 is not in the last column, the horizontal positions of Tile 0 and Tile i are equal and Tile i is to the right of Tile 0 (v[i] = v[0] + 1), OR, if the action move is left, Tile 0 is not in the first column, the horizontal positions of Tile 0 and Tile i are equal and Tile i is to the left of Tile 0 (v[i] = v[0] - 1), then horizontal position of Tile i is equal to that of Tile 0.

c. Otherwise, remain in the same position.


We have defined our goal as the conjunction of positions of all the tiles according to the final configuration, and the CTL formula as !EF(goal), which is "Always, globally the defined goal is false". When the code is run, it will verify whether the specification is True or False. If the specification is False, it will output a counter example to prove it.
