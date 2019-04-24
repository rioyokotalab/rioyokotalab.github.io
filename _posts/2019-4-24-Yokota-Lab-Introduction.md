YOKOTA Laboratory is a research laboratory under the Global Scientific Information and Computing Center, Tokyo Institute of Technology. Located in the Ookayama Campus of Tokyo Institute of Technology, the lab is supervised by Dr. Rio Yokota, an Associate Professor at GSIC, Tokyo Institute of Technology. The lab members consist of undergraduate as well as graduate students.

Research in our lab focuses on the development of software infrastructure and algorithms for next-generation supercomputers. We conduct research on the topics of high-performance computing and its application to scientific computation and machine learning. In particular, we focus on hierarchical low-rank approximation methods such as the fast multipole method (FMM) and H-matrices. Application areas range from classical molecular dynamics to machine learning.

We have several study groups on topics ranging from High-Performance Computing, Fast Multipole Method (FMM), Hierarchical Matrices, Statistical Learning, Computer Vision, and Information Geometry. Each group has a weekly meeting where we discuss related research articles and insights for future research.

## Study Groups

### Hierarchical Matrix

Hierarchical Matrix (often abbreviated as H-Matrix) is a data structure that is used to compress (structured) dense matrix in a data-sparse way. It could approximate a dense matrix which is usually stored entrywise in O(N<sup>2</sup>) by requiring only O(Nklog(N)) units of storage, where k is the parameter that controls the accuracy. Moreover, the complexity of matrix arithmetic operations such as multiplication, inversion, and factorization becomes O(Nlog<sup>p</sup>(N)) when using H-Matrix representation. This is a very powerful tool when N is large.

In the H-Matrix research group, we're working on fast approximate methods for matrix calculations. In particular, these methods are used in physical simulations, boundary integral equations and possibly in second-order optimization of neural networks. We are also developing a framework for hierarchical low-rank matrix approximation that is intended to be a highly parallelized, GPU-accelerated replacement for BLAS when full precision is not needed.

### Fast Multipole Method

The Fast Multipole Method (FMM) is a fast algorithm for rapidly evaluating all pairwise interactions in a system of N electrical charges. First introduced in 1987 by Rokhlin and Greengard (“A Fast Algorithm for Particle Simulations”) FMM has been ranked among the top 10 algorithms of the 20th century. It reduces the computational cost from O(N<sup>2</sup>) to O(N) by clustering the system in bigger and bigger groups and it uses multipole expansions to approximate the potential produced by those groups. 

FMM is applicable to any situation where a large number of objects interact with one another, such as stars in a galaxy, atoms in a protein systems or red blood cells in an artery.
In the FMM research group we focus on:
- Classical FMM
- Translation operators optimization techniques (e.g. PVFMM)
- Parallel implementation of FMM
- Advantages and disadvantages of FMM comparing with other methods
- FMM for periodic boundary value problems 
- FMM and H-matrices

### High-Performance Computing

High-Performance Computing (HPC) is the practice of using high-performance computing resources (i.e. supercomputers) to solve complex computational problems in a way that could yield much higher performance than using a typical desktop computer or workstation. HPC is usually used to solve computational problems that are impractical to solve on a single machine, given the limited amount of computer memory and processing power. Some examples are computational biology, fluid dynamics, and numerical analysis. Such problems are solved by utilizing multiple computing devices and parallel processing techniques.

The HPC study group aims at exploiting hardware performance to develop scalable software using microbenchmarks and profilers. Furthermore, we focus on:
- NVIDIA CUDA and its technologies
- Massively parallel GPU environments such as ABCI and TSUBAME 3.0
- Optimization of inter-GPU communication

### Statistical Learning

In statistical learning theory, the term “statistical learning theory” is used in a broad sense, as it discusses problems such as the meaning and legitimacy of learning methods and their optimality.

Statistical learning theory is a system of theories for mathematically clarifying the nature of machine learning such as deep learning and making use of the new findings obtained there for constructing new methods.

In particular,  we focus on the study of algorithms for learning data and aim to understand the probabilistic behavior of learning algorithms through their background and probabilistic considerations.
In the statistical learning theory research group we focus on:
-Learning Theory
-Statistical Learning
-Probabilistic Optimization
-Continuous Optimization
-Variational Bayes

### Information Geometry

Information geometry is an interdisciplinary field for visual understanding of various problems in information processing. It was proposed by Amari in the 1980s. It is a study that spans not only information theory but also statistics and system theory, and helps to understand theory and algorithms in a unified way.

For example, learning in machine learning is equivalent to the transition of probability distribution, but the information geometry reveals the geometrical relationship between probability distributions. This makes the learning structure transparent and makes it possible to improve learning for speeding up by reducing the number of iterations and so on.

The application examples are not limited to machine learning, but include a wide variety of signal processing and neural networks.
Information geometry is related to the following mathematical terms:
 - Euclidean space, Riemann space
 - Manifold, divergence
 - Legendre transformation, duality
 - Curvature, torsion
 - Fisher information, natural gradient method
 - Clustering, principal component analysis
