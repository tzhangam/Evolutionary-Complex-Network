# Ideas

---

***Edge tension Metropolis method***

For my community detection based on simulation, I have some thought to implement it using metropolis algorithm on my way to Diana Porter. **That is the tension in the string should be treated as extra potential increase**, that the further 2 connected edge are, the potential increases more. Then other setting, **the positive charge repulsion, we can only consider the neighborhood effect**, and we provide **initial temperature** for the vertices to diffuse, and **keep the temperature high enough so that the separation of vertices is in good shape**. Now the whole picture will be exactly as what KMC is doing, which I did in UROP1000, and adding new edge and vertices will be easy.

---

***Weighted Flood Fill Method for community detection in static network***

Imaging the network as a gravitational landscape, with heavily connected parts having deeper gravitational potential. If I flood fill the landscape, the water is likely to stays in the lower parts to become a pond.

So the idea is to DFS the network, 

Method 1: but only dives in when the degree of the node is high enough. 

Method 2: the probability of diving in is proportional to the degree of the node.

Method 3: dive in each node un-conditionally, shrink back when the degree of the node becomes to low.

Method 4: the probabilistic version of method 3, mimicking method 2.

Note Method 1 and 3 are dual of each other. 