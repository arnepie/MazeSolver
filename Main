import random
import matplotlib.pyplot as plt


def create_maze(dim):
    maze = [[1 for _ in range(dim * 2 + 1)] for _ in range(dim * 2 + 1)]

    y, x = 1, 1
    maze[y][x] = 0

    stack = [(y, x)]

    while stack:
        y, x = stack[-1]
        directions = [(0, 2), (2, 0), (0, -2), (-2, 0)]
        random.shuffle(directions)

        for dy, dx in directions:
            ny, nx = y + dy, x + dx
            if dim * 2 > nx > 0 and dim * 2 > ny > 0 and maze[ny][nx] == 1:
                maze[ny][nx] = 0
                maze[y + dy // 2][x + dx // 2] = 0
                stack.append((ny, nx))
                break

        else:
            stack.pop()

    maze[1][0] = 0
    maze[dim * 2 - 1][dim * 2] = 0

    return maze


def draw_maze(maze):
    dim_y = len(maze)
    dim_x = len(maze[0])

    fig, ax = plt.subplots(figsize=(dim_x // 2, dim_y // 2))

    for y in range(dim_y):
        for x in range(dim_x):
            if maze[y][x] == 1:
                ax.add_patch(plt.Rectangle((x, y), 1, 1, color='black'))
            else:
                ax.add_patch(plt.Rectangle((x, y), 1, 1, color='white'))

    ax.set_xlim(0, dim_x)
    ax.set_ylim(0, dim_y)

    ax.set_xticks([])
    ax.set_yticks([])

    plt.gca().invert_yaxis()

    plt.show()


dimensions = 10
maze = create_maze(dimensions)
draw_maze(maze)
