<p>
<h1> Description </h1>
Our agent is designed to learn about corresponding relationship between terrain blocks and objects on it, and it will apply what it has learnt in a more complex map to find objects it is asked for. It is like an auto-robot for searching required objects in places that human cannot reach, such as deep forest or seafloor. It will optimize its path while it is searching. 
On the right side is a training map, which is divided into four pieces with objects on it. Most objects are bind onto a certain type of block, but there are outliers just to confuse our agent. Expect some unexpected. 
Our agent traverses the training map via depth-first algorithm. It will learn that pumpkins are on sandstone; eggs are on diamond, and so on. 
</p>

<p>
<h2>Training Map:</h2>
Here we use the recipe for pumpkin pie as an example. To craft a pumpkin pie, we need egg, sugar, and a pumpkin. On the training map, eggs are created on Diamond_block, apples on grass, sugar on glass, and pumpkins on sandstone. However, there are cookies and cooked fish as outliers on random position on the map. Out agent will traverse the training map to learn about this policy. As it learns, it will know to find apples on grass first and so as other relationships. It will bring what it has learnt to the test map. 

<img src="docs/Photos/training_map.png" alt="Training map" style="width: 80%;" >
</p>

<p>
<h2>Test Map</h2>
After that, our agent is put at the right corner on a randomly generated test map, which is a 27 by 27 map concluding 81 groups of different blocks, and not every block has its assigned objects. Obsidian and apple are considered outliers here. 
The agent is using A-star search to evaluate four steps ahead of its current location, and return a potentially best direction. The agent ranks those blocks on various standards, including the worthy status of this block (visited, unvisited but not valuable, and potentially valuable) and the path of this block (how many steps have to be made to move to this block). The challenging part is that the priority changes as every step it takes and items it finds. For example, if we are looking for pumpkin, we will look for sandstones. All sandstones are potentially valuable to us untill one pumpkin is found, and then all sandstone are treated as unvisited but not valuable blocks, which means lower rank. All blocks are important to us in the first place, but they get less valuable as the agent travels. However, the visited blocks are not forbidden because there are chances that the agent has to pass through it to get to another potentially valuable block. Therefore, we give different scores to those situation carefully. In addition to that, visted blocks tend to be less and less possible to take. 
<img src="docs/Photos/test_map.png" >
</p>


<p>
<h2>Raw Data</h2>
 [("egg", "diamond_block"), ("apple", "grass"), ("sugar", "glass"), ("pumpkin", "sandstone"), ("apple", "obsidian")]
 
Random	
[521, 61, 146, 38, 36, 439, 143, 240, 29, 93]
Max = 521 Min = 29  AVG = 174.6	SD = 165.718556595

DFS
[42, 14, 68, 67, 16, 69, 82, 55, 70, 42, 69]
Max = 82  Min = 14  AVG = 54.0	SD = 21.7171905097

A* (Our)
[12, 14, 6, 14, 24, 22, 26, 22, 20, 19]
Max = 26  Min = 6 AVG = 17.9	SD = 5.90677577025

</p>