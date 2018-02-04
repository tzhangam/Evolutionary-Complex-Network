##Recommended studies on network dynamics

[2]S.N. Dorogovtsev and J.F.F. Mendes. Handbook of Graphs and Networks: From the Genome to the
Internet, chapter Accelerated growth of networks. Wiley-VCH, 2002.
[3] J. Leskovec, J. Kleinberg, and C. Faloutsos. Graphs over time: Densification laws, shrinking diameters
and possible explanations. In ACM SIGKDD, 2005.
[4] G. Palla, A. Barabasi, and T. Vicsek. Quantifying social group evolution. Nature, 446:664–667, April
2007.

---

##A popup thought of mine.

My analysis: Average distance between 2 nodes in a random graph: $$|V|^2/(2|E|)$$. Using Possion expected waiting time argument.

---

##Community detecion methods is likely to be a gaint topic, I have downloaded the list of methods existing, hopefully I have come up with a brand new one, which is positive charge plus rubber band, simulation based, incrementally updatable.

---

## Some current principles of network evolution study

I.	Snapshot view: The dynamic network is a sequence of static network

II.	Time series view: The dynamic network can be characterize as multi-thread time series of local parameters, like rate of edge creation, node creation, etc.

III.	Special phenomena and concrete context application

---

## Comments

"Many studies have been focused on static networks, therefore the first approach is the
more developed, however the definition of proper **time scales** is a unsolved problem and
there is no warranty that such time scales can be defined in an automatic way given
an evolving network. **For both other approaches, much work has to be done in order to**
**define new relevant parameters to describe the evolution as precisely as possible.**
Finally, using all the parameters obtained with the previous approaches would allow
the introduction of evolutionary models for dynamic complex networks. Such models
could be used in formal contexts and for simulation purposes. Defining random models is
not an easy task and even for static networks some simple parameters cannot be captured
in a satisfactory way."

