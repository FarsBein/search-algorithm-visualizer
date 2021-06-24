# Search Algorithm Visualizer
An interactive and fun search algorithm visualizer that compares BFS to DFS. 

# General Facts
DFS and BFS worst case have the same time complexity, O(V+E) = O(n). However, they are used differently depending on the situation.

BFS consumes more memory and is slower generally compare to DFS, but in return it gives the most optimum path.

DFS however can go indefinitely if the size of graph is infant. 

# Showcase

### Solved maze using Depth First Search (DFS) vs using Breath First Search (BFS)
<img src='https://user-images.githubusercontent.com/53714581/122844973-bbc1c180-d2d0-11eb-8e15-24452308a676.JPG' width=480/> <img src='https://user-images.githubusercontent.com/53714581/122844976-bbc1c180-d2d0-11eb-8e06-8725c51a861f.JPG' width=480/>

<!-- ### Using Breath First Search BFS -->
<!-- ![3](https://user-images.githubusercontent.com/53714581/122844976-bbc1c180-d2d0-11eb-8e06-8725c51a861f.JPG) -->

# The Algorithms

For BFS, I used Queues to track visited/unvisted nodes and used come_from to track the final path. 
```
    queue = Queue()
    
    queue.put(start)

    came_from = {} 
    
    curr_node = None
    
    while not queue.empty():
        # maintain the color of start and end nodes
        start.make_start()
        end.make_end()
        
        curr_node = queue.get()
    
        if curr_node == end:
            draw_path(lambda_draw,came_from, curr_node) # curr_node = end, so either can work
            start.make_start()
            break
        
        for neighbor in curr_node.neighbors:
            if not neighbor.is_visited() and not neighbor.is_barrier():
                neighbor.make_visited()
                queue.put(neighbor)
                came_from[neighbor] = curr_node
                lambda_draw()
        time.sleep(.03)
        
        # GUI functionalities
        for event in pygame.event.get():
            # exit while solving 
            if event.type == pygame.QUIT:
                pygame.quit()
            # end solving
            if event.type == pygame.KEYDOWN:
                    if event.key == pygame.K_SPACE:
                        queue = Queue()
```

For DFS, I used Stack to track visited/unvisted nodes and used come_from to track the final path. 
```
    queue = Queue()
    
    queue.put(start)

    came_from = {} 
    
    curr_node = None
    
    while not queue.empty():
        # maintain the color of start and end nodes
        start.make_start()
        end.make_end()
        
        curr_node = queue.get()
    
        if curr_node == end:
            draw_path(lambda_draw,came_from, curr_node) # curr_node = end, so either can work
            start.make_start()
            break
        
        for neighbor in curr_node.neighbors:
            if not neighbor.is_visited() and not neighbor.is_barrier():
                neighbor.make_visited()
                queue.put(neighbor)
                came_from[neighbor] = curr_node
                lambda_draw()
        time.sleep(.03)
        
        # GUI functionalities
        for event in pygame.event.get():
            # exit while solving 
            if event.type == pygame.QUIT:
                pygame.quit()
            # end solving
            if event.type == pygame.KEYDOWN:
                    if event.key == pygame.K_SPACE:
                        queue = Queue()
```

# Insulation

1- copy this repostery

2- Inside the Command Prompt type ```pygame window.py```

3- Enjoy

or

use find the package in PyPi https://pypi.org/project/DFS-BFS-visualizer/


# Instruction on how to use
- Left click to draw on window and Right click to Erase 
- You have to draw the start and end node firsts before barrier
- Press D to solve using DFS
- Press B to solve using BFS
- Press R to remove the solving lines and maintain the drawing made by you
- Press space to remove everything
