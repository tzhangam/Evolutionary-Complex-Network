## Further Comments on How to describe a dynamic network

I believe to characterize the global structure of a graph at a given instance of time is as hard as solving the graph isomorphism problem, identification is seeking a way to determine isomorphism after all. With rewiring of even one single edge, the isomorphism can be totally different. And determining an isomorphism is rather expensive.

The hope remains in whether small changes in big graphs do not alter the global isomorphism too much, so comes the idea of dynamic character study. Then this idea abandon the global picture so is not going to work that well in terms of describing the evolution of a graph.

My first view: it makes more sense to spend time determining isomorphism, rather than mining dynamic patterns, the former achieves accuracy and is the key to construct a good theory and good understanding of graph evolution.

------

The difficulty in determining graph isomorphism brings me to think about possible solutions. 

First thought is when building a graph from void to being, we follow strict non-symmetric construction rule, such as add by weight or by rotation, to break isomorphism finding into natural automorphism finding.

Next thought is to tackle the isomorphism from extra dimensions, like introducing embedding landscape, or source node and target node.

A final thought is to use taylor-made description to tackle characteristics of our interest, only retrieving the information we need.