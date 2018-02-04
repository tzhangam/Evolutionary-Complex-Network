# Reading Target of Community Detection

---

* The definition or good description of the community object.

* The problem statement of community detection: input, premise, goal.

  ​

  ​

  ##Definitions

  ---

  From ***Mutual Friend Coefficient***:

  *"In this article, we highlight another property that is found in many networks, the property of community structure, in which network nodes are joined together in tightly knit groups, between which there are only looser connections."*

  *"...subsets of vertices within which **vertex–vertex connections are dense**, but between*
  *which connections are less dense..."*

  *"...the **centrality** and influence of nodes in networks..."*

  - Remark: this paper distinguishes community by the density of edges in the landscape of the graph. If not for the graph is in a discrete space, I believe we can define a gradient field of edge density over vertex space, which is basically the degree distribution over the graph. 

  - More specifically, with only vertices, we can define the scalar function: 

    $$d: V \rightarrow N, d(v)=degree\ of\ v$$ 

     of degree at each point of vertex. With vertices and edge, we can define the "directional derivative" of this dunction d:

    ​		$$ d':G \rightarrow Q, d'(v,e)=\frac{d(v+e)-d(v)}{w(e)} $$

    where (v,e) is a vertex-edge pair in graph G, v+e is the vertex v' at the other end of v, and w(e) is the weight on edge e.

    Then the density of vertex-vertex connections can be view using d and d' functions. In a community, d should be large, and d' should be close to 0, that is like a plateau in the graph landscape. Most importantly d should be large. And we can also define the "total differential" of v by summing up d' in all directions, so that the description can be more homogeneous. 

    **The only concern on this construction is whether in d', the devision by w(e) makes sense or not, I will come back to this later.**

    As a reminder, the gradient description is still based on static graph framework.

  *From **IntroToCommunityDetection**:*

  The definition of internal, external degrees. The idea is heavily based on clustering theory.

  ![IntExtDegree](C:\Users\tzhangam\Desktop\Evolutionary-Complex-Network\Community Detection papers\IntExtDegree.JPG)