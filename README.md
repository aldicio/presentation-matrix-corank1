<!DOCTYPE html>
<html>
<head>
<style>
p {
    font-size: 20px;
	text-align: justify;
}
	ol{
		font-size: 20px;
		text-align: justify;
	}
 </style>
<!-- INICIO SCRIPT LATEX -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.1/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>
<script type="text/javascript">MathJax.Hub.Config({
  tex2jax: {inlineMath: [['$','$'],['[m]','[/m]']], displayMath: [['[mm]','[/mm]'],['$$','$$']]},
  "HTML-CSS": { scale: 100, showMathMenu: false, minScaleAdjust: 100}
});</script>
<!-- FIM SCRIPT LATEX -->
</head>
<body>
<h2>A presentation matrix associated to discriminant of co-rank one maps from ${\mathbb C}^n$ to ${\mathbb C}^n$.</h2>
<p>	
Aldicio J. Miranda and Marcelo J. Saia	
<br/>
<br/>
<strong>Abstract:</strong>
<br/>
<br/>
	
Given a finite corank 1 map germ $f$ in ${\mathcal O}_{n,n}$, the objective of this article is the construction of a presentation matrix of
the ring of the critical locus as an ${\mathcal O}_n$-module via $f^*$. To this end, we use a general algorithm of Mond and Pellikaan and apply it directly to our case. The application of this algorithm in general is not an easy task and it is a challenge to find the presentation matrix, even in simple cases. However, for the maps considered here we  present a fast implementation of the algorithm of Mond and Pellikaan,  moreover we implement this construction using the
software  Maple and Singular, showing explicitly how to compute the elements of the presentation matrix for such maps.
Then we show how to apply this construction to obtain invariants associated to the isolated stable singularities of such germs, called  $0$-stable ingularities.
<br/>
<br/>
<strong>Introduction</strong>
<br/>
<br/>
A presentation of  an $R$-module $M$ ($R$, a commutative ring with unit)  is
an exact sequence
\begin{equation}\label{seqExata}
{R}^{p} \stackrel{\lambda}{\longrightarrow} {R}^{q} \stackrel{\alpha}\longrightarrow {M}
\longrightarrow 0
\end{equation}
of $R$-modules, when $M$ is finitely presented such a presentation always exists and $\lambda$ is called a presentation matrix of relations among the generators of the module.


In general it is not easy to construct  a presentation, but when $(X,x)$ is the multi-germ of a
Cohen-Macaulay variety of dimension $n$, Mond and Pellikaan in [1], showed an algorithm for constructing
the presentation of the ${\mathcal O}_{n+1}$-module ${\mathcal O}_{(X,x)}$ for finite analytic map germs
$f:(X,x) \to ({\mathbb C}^{n+1},0)$.

The main problem when using this algorithm is that you need to know some coefficients $\alpha_{j}^{i}$
in order to construct the presentation, but this is not easy in general. In this paper we give an explicit construction of the coefficients
$\alpha_{j}^{i}$ for the case that the variety is the singular locus of a map germ of corank 1 and then, follow the
Mond-Pellikaan construction in order to obtain the  presentation matrix.

To apply this algorithm it is necessary that the map germ $f$ is given in the so called prenormal form, or choosing linearly adapted coordinates, we can write
$f(x, z) = (x_1, \ldots , x_{n-1}, g(x, z))$, where $x = (x_1, \ldots , x_{n-1}) \in {\mathbb C}^{n-1}$, $z \in {\mathbb C}$ and $g : ({\mathbb C}^n, 0) \to
({\mathbb C},0)$ is a polynomial that can be written in the form $$g(x,z)=z^{k+1}+h(x,z),\ {\rm with} \ h(x,z)=h_{k-1}(x)z^{k-1}+h_{k-2}(x)z^{k-2}+\cdots h_{1}(x)z+h_0(x),$$ with
$h_i(0)=0$ for all $h_i : ({\mathbb C}^{n}, 0) \to ({\mathbb C},0)$, $i=0,\ldots ,k-1$.

 The main importance of this construction is related to the study of
 the analytic invariants of the map germ $f$, given in terms of the multiple point schemes of its
restriction to the critical locus of $f$, and these spaces can be computed
by means of the Fitting ideals of the  presentation matrix.

 Moreover  we implement this construction using the  software Maple and Singular, showing explicitly how to compute the elements of the matrix $\lambda$
 for such maps. Then we show how to apply this construction to obtain some invariants
 associated to the singularities of map germs in this ring.
<br/>
<br/>
<strong>Procedure to obtain the presentation matrix $\lambda$</strong>
<br/>
<br/>
We describe here the algorithm  given by Mond and Pellikaan in [Section 2.2, 1] to construct the presentation of any ${\mathcal O}_{n+1}$-module $f_{*}{\mathcal O}_{X}$.

Denote by ${\mathcal O}_n$ the local ring of holomorphic function germs $h : ({\mathbb C}^n, 0) \to {\mathbb C}$  and ${\mathcal O}_{(n,n)}$ denotes the module of holomorphic map germs $f:({\mathbb C}^n, 0) \to {\mathbb C}^n$.

Let $(X,x)$ be  the multi-germ of a Cohen-Macaulay variety of dimension $n$ and $f:(X,x) \to ({\mathbb C}^{n+1},0)$ be the germ of a finite analytic map,
by the Weierstrass preparation theorem it follows that ${\mathcal O}_{(X,x)}$ is a finite ${\mathcal O}_{n+1}$-module via the function $f^*$.

 To compute the matrix $\lambda$,  we remark that if the classes of $g_1,g_2,\ldots,g_h$ in $\frac{{\mathcal O}_{(X,x)}}{f^*{\mathfrak m}_0}$ generate it as a
vector space over ${\mathbb C}$, then $g_1,g_2,\ldots,g_h$ generate ${\mathcal O}_{(X,x)}$ as an ${\mathcal O}_{n+1}$-module,
therefore it is enough to obtain the relations among the $g_i$, $i=1,\ldots, h$ over ${\mathcal O}_{n+1}$.

<br/>
<br/>

Choose a projection  $\pi:({\mathbb C}^{n+1},0) \to ({\mathbb C}^{n},0)$ such that $\widetilde{f}=\pi \circ f$ is also finite.
After a change of coordinates we suppose that $f(x)=(\widetilde{f}(x), f_{n+1}(x))$ and as ${\mathcal O}_{X,x}$ is Cohen-Macaulay, then
${\mathcal O}_{X,x}$ is a free  ${\mathcal O}_{n}$-module via $\widetilde{f}^*$.


Then for all $i,j$ with $1\leq i,j \leq h$ there exist unique $\alpha_j^i \in {\mathcal O}_{n}$,  such that
\begin{equation}\label{eq2}
g_j\cdot f_{n+1}=\sum({\alpha_j^i \circ \widetilde{f}}) \cdot g_i.
\end{equation}

As the germs $g_i$ generate ${\mathcal O}_{X,x}$ over ${\mathcal O}_{n+1}$ via $f^*$, then
$$\lambda_j^i=\alpha_j^i \circ \pi, \ \ i\neq j$$
$$\lambda_i^i=\alpha_i^i \circ \pi-X_{n+1},$$
since $f_{n+1}=X_{n+1} \circ f$ and  $(X_1, \ldots, X_{n+1})$ denotes the coordinates of  ${\mathbb C}^{n+1}$ in the target.

Therefore one has the matrix $(\lambda) = \left ( \lambda^{i}_{j}\right )$ for the exact sequence of the
${\mathcal O}_{n+1}$-module ${\mathcal O}_{X,x}$. \begin{equation}\label{seqExata2}
{\mathcal O}_{n+1}^{p} \stackrel{\lambda}{\longrightarrow} {\mathcal O}_{n+1}^{q}
\stackrel{\alpha}\longrightarrow {\mathcal O}_{X,x} \longrightarrow 0
\end{equation}

If  $g_1,g_2,\ldots,g_h$ generate ${\mathcal O}_{X,x}$, we can consider  $g_1=1$, $q=p=h$ and the
matrix $\alpha$ is given in such a way that $\alpha(e_i)=g_i$, where  $e_i$ is the  $i^{th}$ element of the usual basis.

<br/>
<br/>
<strong>Implementation</strong>
<br/>
<br/>
<a href="https://drive.google.com/open?id=1_kCkbZmlcVScKe8LNtbJuPITyOJKsDxQ">prescorank1.lib</a>
<br/>
<br/>
For this case with $f$ in its pre-normal form is possible to get a presentation without use groebner bases, [2], 
and moreover we  present a fast implementation in Maple and Singular (prescorank1.lib) of the algorithm of Mond and Pellikaan, showing explicitly how to compute the elements of the polynomial presentation matrices for such maps.
<br/>
<br/>
<strong>Example:</strong>
Let $f:({\mathbb C}^3,0) \to ({\mathbb C}^3,0)$ be defined by $f(x,y,z)=(x,y,z^6+xz+yz^2).$ 
<br/>We have that $\frac{{\mathcal O}_{(\Sigma(f),0)}}{f^{*}\mathfrak{m}_{({\mathbb C}^3,0)}}\cong \frac{{\mathbb C}\{z\}}{z^5}$ and ${\mathcal O}_{(\Sigma(f),0)}$  is finitely generated as ${\mathcal
O}_3$-module via $f^{*}$.
<br/>
How to obtain the matrix of a presentation for this map?
<br/>
<br/>	
$>$ LIB "prescorank1.lib";
<br/>
> ring r=0,(x,y,z),ds;
<br/>
> ideal f=x,y,z6+yz+xz2;
<br/>
> prescorank1(f);
<br/>

//     PM
<br/>
//R^h------>R^h------>Ox------>0;  h = 5, R = Local target ring with variables:(x,y,Y).
<br/>

Y,     -5/6y, -2/3x,0,    0,    
<br/>
0,     Y,     -5/6y,-2/3x,0,    
<br/>
0,     0,     Y,    -5/6y,-2/3x,
<br/>
1/9xy, 2/9x2, 0,    Y,    -5/6y,
<br/>
5/36y2,7/18xy,2/9x2,0,    Y     
<br/>

//TOTAL TIME = 0 sec
<br/>

//To access the presentation matrix PM, type:  setring RT; PM; 
<br/>
$$PM=
\left(
\begin{array}{*{5}{c}}
Y & -\frac{5}{6}y & -\frac{2}{3}x & 0 & 0 \\
0 & Y & -\frac{5}{6}y & -\frac{2}{3}x & 0 \\
0 & 0 & Y & -\frac{5}{6}y & -\frac{2}{3}x \\
\frac{1}{9}xy & \frac{2}{9}x^{2} & 0 & Y & -\frac{5}{6}y \\
\frac{5}{36}y^{2} & \frac{7}{18}xy & \frac{2}{9}x^{2} & 0 & Y
\end{array}
\right)
$$
> setring RT;
<br/>
> ideal F0=fitting(PM,0);F0;
<br/>
F0[1]=46656Y5+3125y6+22500xy4Y+43200x2y2Y2+13824x3Y3+256x5y2+1024x6Y
<br/>
> ideal F1=fitting(PM,1);F1;
<br/>
F1[1]=1875y4+5400xy2Y+1728x2Y2+256x5
<br/>
F1[2]=1125y3Y+2160xyY2-64x4y
<br/>
F1[3]=675y2Y2+648xY3+40x3y2+96x4Y
<br/>
F1[4]=405yY3-25x2y3-84x3yY
<br/>
F1[5]=1944Y4+125xy4+540x2y2Y+288x3Y2
<br/>
> ideal F2=fitting(PM,2);F2;
<br/>
F2[1]=x3
<br/>
F2[2]=x2y
<br/>
F2[3]=xy2
<br/>
F2[4]=y3
<br/>
F2[5]=x2Y
<br/>
F2[6]=xyY
<br/>
F2[7]=y2Y
<br/>
F2[8]=xY2
<br/>
F2[9]=yY2
<br/>
F2[10]=Y3
<br/>
> vdim(std(F2));
<br/>
10
</p>
<ol><li> $V(F_0) = \Delta(f)$ (discriminant set of f).</li>
	<li>$V(F_1) = A_{2}(f) \cup A_{1,1}(f)$ (cuspidal curve $\cup$ ordinary double points curve).</li>
	<li>$V(F_2) = A_{3}(f) \cup A_{2,1}(f)\cup A_{1,1,1}(f)$ (swallowtail $\cup$ double fold with cuspidal points $\cup$ triple fold points).</li>
	</ol>
As $vdim(std(F2)) = 10$, then this germ has $10$ zero-stables singularities in a stable deformation.
<p>
[1] D. Mond and R. Pellikaan, Fitting ideals and multiple points of analytic mappings. Algebraic geometry and complex analysis
(Patzcuaro, 1987), 107--161, Lecture Notes in Math., Springer, Berlin, (1989), 1414.
<br/>
[2] Miranda, A. J., Saia, M. J., A presentation matrix associated to the discriminant of a co-rank one map germ from $\mathbb {C}^n$ to $\mathbb {C}^n$,
Contemporary Mathematics, 675 (2016) 241-252.
	
</p>
</body>
</html>
