# Two Dice Done Rigorously: Sigma-Algebras, Pushforward Measures, Random Variables, and Why 7 Wins (Part 3 of 3)

Not by ai badges will eventually go here

![alt text](image.png)
*This is the third and final installment in the series. I highly recommend reading both the first and second if you haven't already:*
- *Part 1: https://medium.com/@mckenzieben15/two-dice-done-rigorously-sigma-algebras-pushforward-measures-random-variables-and-why-7-wins-0379d5513631*
- *Part 2: https://medium.com/@mckenzieben15/two-dice-done-rigorously-sigma-algebras-pushforward-measures-random-variables-and-why-7-wins-0379d5513631*
## Brief Recap
In the first article we learned about the probability space tuple, that our probability space is a measurable space equipped with a probability measure, and what a sigma algebra on a set is. In the second article, we learned about preimages and measurable functions, and how a random variable is a measurable function from the measurable space (comprised of the sample space and event space), to the measurable space of adding our dice rolls together. We finished that article off with an example relating all the concepts together.

In this article, we will tie all the concepts we've used together, and **finally** answer our question: *"Why does 7 win when rolling two dice and taking their sum?"*

## A Closer Look at Measures
We need to take a closer look at measures in order to have a smooth ride in this article. This will be restating things we've already learned, but having them here will make this process easier.
### Axioms of Measures
First, if you are asking the question, **What is an axiom?** Don't worry. Although the study of axioms is a deep topic in philosophy, for our purposes we only need to know that **axioms are logically consistent rules which we agree upon**.

Recall from the first article that a measure is a function that goes from a sigma to the interval of positive numbers:
$$
\mu:\Sigma\rightarrow[0,\infty]
$$
*Figure 11 from Article 1*

Where the measure adheres to the following two rules:
$$
\begin{aligned}
&1.\ \mu\left(\bigcup_{i=1}^\infty A_i\right)=\sum_{i=1}^\infty\mu(A_i)\text{ where all }A_1,A_2\dots\in\Sigma\text{ are pairwise disjoint}\\
&2.\ \mu(\emptyset)=0
\end{aligned}
$$
*Figure 12 from Article 1*

These rules and definition are the axioms of a measure.
### Useful Lemma of Measures: Finite Additivity
Here we go introducing more vocabulary words into the mix. **What is a lemma?** Axioms are the statements we take as a given, the rules we define. **A lemma is a logical consequence of those axioms which ends up being a useful stepping stone to further the conversation**. Here, we will prove the lemma of finite additivity of measures, and will end up using the lemma later in this article. Observe that rule 1 from figure 12 of our first article goes to infinity:
$$
1.\ \mu\left(\bigcup_{i=1}^\infty A_i\right)=\sum_{i=1}^\infty\mu(A_i)\text{ where all }A_1,A_2\dots\in\Sigma\text{ are pairwise disjoint}
$$

**That isn't finite!** Although it might seem obvious that the finite version follows, we are doing math here, and in math we have to be pedantic. Fortunately our proof isn't complicated. Basically, we simply take a set of non empty elements of our sigma algebra that is finite. Then we append an infinite number of empty sets at the end. Finally, when we take the inifinite union of this set, it collapses to the finite set of sigma algebra elements we actually care about. Formally the proof can be stated as follows:

$$
\begin{aligned}
&\text{Claim: Let }(X,\Sigma,\mu)\text{ be a measure space}, n\in\mathbb{N},\text{ and }A_1,A_2\dots A_n\in\Sigma\text{ be }\\
&\hspace{3em}\text{ pairwise disjoint. Then: }\mu\left(\bigcup_{i=1}^n A_i\right)=\sum_{i=1}^n\mu(A_i)\\
&\text{Proof:}\\
&\hspace{3em}1. \text{ Define the sequence of sets: }\left(A_i\right)_{i\in\mathbb{N}},\text{where }A_1\dots A_n\text{ are the sets}\\
&\hspace{4em}\text{from our claim, and }A_i=\emptyset\text{ for }i>n\\
&\hspace{3em}2.\text{ By definition of sigma algebra: }\emptyset=X^c\in\Sigma\text{ and }X\in\Sigma\text{ so all }A_i\in\Sigma.\\
&\hspace{4em}\text{This step simply shows that }\emptyset\in\Sigma\text{ so the extended sequence stays inside }\Sigma.\\
&\hspace{3em}3.\text{ All sets in our sequence from point 1 are pairwise disjoint:}\\
&\hspace{4em}\text{The first }n\text{ sets are by our claim. The remaining sets are pairwise disjoint by}\\
&\hspace{4em}\text{the fact that }\emptyset\cap A=\emptyset\text{ for any set } A\text{ and all remaining sets are }\emptyset\\
&\hspace{3em}4.\text{ By the axiom of sigma additivity of measures, and point 3:}\\
&\hspace{4em}\mu\left(\bigcup_{i=1}^\infty A_i\right)=\sum_{i=1}^\infty\mu(A_i)\\
&\hspace{3em}5.\text{ By our sequence definition in point 1: }\\
&\hspace{4em}\bigcup_{i=1}^\infty(A_i)=\left(\bigcup_{i=1}^nA_i\right)\cup\left(\bigcup_{i=n+1}^\infty A_i\right)=\left(\bigcup_{i=1}^n A_i\right)\cup\emptyset=\bigcup_{i=1}^n A_i\\
&\hspace{3em}6.\text{ By properties of summation: }\sum_{i=1}^\infty a_i=\sum_{i=1}^n a_i+\sum_{i=n+1}^\infty a_i\\
&\hspace{4em}\text{Note that since our measure is nonnegative by definition, all values}\\
&\hspace{4em}\text{in our sum are in }[0,\infty], \text{which makes our sum well defined. We don't}\\
&\hspace{4em}\text{worry about any cases of undefined: }\infty-\infty\\
&\hspace{3em}7.\text{ For }i>n,\ A_i=\emptyset.\text{ Therefore, }\mu(A_i)=0\text{ for }i>n\text{ by the nullset axiom of}\\
&\hspace{4em}\text{measure: }\mu(\emptyset)=0\text{ and by 6, we can split our sum at }n.\text{ Hence:}\\
&\hspace{4em}\sum_{i=1}^\infty\mu(A_i)=\sum_{i=1}^n \mu(A_i)+\sum_{i=n+1}^\infty\mu(A_i)\text{ and }\sum_{i=n+1}^\infty\mu(A_i)=0,\text{ so }\\
&\hspace{4em}\sum_{i=1}^\infty\mu(A_i)=\sum_{i=1}^n\mu(A_i)+0\\
&\hspace{3em}8.\text{ Substituting 5 and 7 into 4 gives us: }\mu\left(\bigcup_{i=1}^n A_i\right)=\sum_{i=1}^n\mu(A_i)\\
&\hspace{4em}\text{Which is the claim. }\blacksquare
\end{aligned}
$$
*Figure 1*
### Definition: Set Equality
If you couldn't already tell, we need some set theory to make this series rigorous. Here we are simply stating a definition: **The definition of set equality**. This is a definition, so we don't prove it. The good news for us? This definition is intuitive.
$$
\begin{aligned}
&\textit{Definition.}\text{ Two sets, }A\text{ and }B,\text{ are said to be equal, written }A=B,\\
&\text{if and only if }\forall x\, (x\in A\iff x\in B)
\end{aligned}
$$
*figure 2*

That's just the fancy math way to say that the two sets have the same elements, and this is when we say the two sets are equal.

**Caveat**: since mathematics requires super specific, precise terminology, it should be noted that **set equality** and **set equivalence** are two different things. (if you are groaning, that's understandable. I did as well when I read this). The distinction isn't too complicated: *set equality* means the two sets contain the *exact same elements*. In contrast, *set equivalence* means that the two sets have the same *cardinality* or size. Understanding equivalence is not necessary for this article, but at a high level we call same-cardinality-sets equivalent since we can make a bridge between the two. *(Seriously you can ignore this if you want to, I felt compelled to mention it though.)*
### Lemma: Demorgan's Law 
Another Lemma! (If you couldn't tell by now math requires you to show your work). We will use our definition of set equality above in our proof of Demorgan's Law.
$$
\begin{aligned}
&\text{Claim: }
\end{aligned}
$$
*figure 3*
# scratch but possibly useful later
## Defining our Probability Measure
To start, we need to define the probability measure of our underlying probability space (the left side of our random variable). We learned in the first article that our underlying probability space is the measure space:
$$
\begin{aligned}
&\hspace{3em}(\Omega,\mathcal{F},\mathcal{P})\\
&\Omega:\text{ is our sample space}\\
&\hspace{1em}\Omega=\{(i,j):i,j\in\{1,2,3,4,5,6\}\}\\
&\mathcal{F}:\text{ is our event space}\\
&\hspace{1em}\mathcal{F}=2^\Omega\\
&\mathcal{P}: \text{ is our probability measure}\\
&\hspace{1em}\text{(more details to follow)}
\end{aligned}
$$
*figure 1*


While we did give an overview of our probability measure and the qualities it has (*figure 14 in article 1*) we didn't actually define what values it takes. Here is where will will do so!

Recall the "rules" that our probability measure adheres to:
$$
\begin{aligned}
&1.\ \mathcal{P}\left(\bigcup_{i=1}^\infty E_i\right)=\sum_{i=1}^\infty\mathcal{P}(E_i)\text{ where all }E_1,E_2\dots\in\mathcal{F}\text{ are pairwise disjoint}\\
&2.\ \mathcal{P}(\emptyset)=0\\
&3.\ \mathcal{P}(\Omega)=1, \text{ the measure of the sample space is } 1\\
&4.\ \mathcal{P}:\mathcal{F}\rightarrow[0,\infty]\text{ (it's a measure and therefore nonnegative)}
\end{aligned}
$$
*figure 14 from article 1*

Note that since we know that the max value our probability measure can take is 1 (by defintion), we know that the smallest value it can take is 0 (if we have an empty set as our event) and we have the property of monotonicity of the probability measure on the size of our sets in the event space, we can restate rule 4 as:
$$
4.\ \mathcal{P}:\mathcal{F}\rightarrow[0,1]
$$

This makes our probability measure rules:
$$
\begin{aligned}
&1.\ \mathcal{P}\left(\bigcup_{i=1}^\infty E_i\right)=\sum_{i=1}^\infty\mathcal{P}(E_i)\text{ where all }E_1,E_2\dots\in\mathcal{F}\text{ are pairwise disjoint}\\
&2.\ \mathcal{P}(\emptyset)=0\\
&3.\ \mathcal{P}(\Omega)=1, \text{ the measure of the sample space is } 1\\
&4.\ \mathcal{P}:\mathcal{F}\rightarrow[0,1]
\end{aligned}
$$
*figure 2*

Now, we know that our sample space is an element of our event space, and we also know that the elements of our event space are subsets of our sample space. The question we want our probabiliy measure to answer is:
$$
\text{What are the chances of }E\in\mathcal{F}\text{ happening?}
$$
### A Bit of Intuition
To build a bit of intuition before defining our probability measure formally, first we can ask ourselves, *how many elements are there in our sample space?*

The answer 36. We arrive at this by noting for every 1st die roll, there are 6 possible ways to roll the second die. Since there are 6 possible ways to roll the first die, we have: 6x6=36.

Since we are using fair dice, with the observation above we know that the chances of getting **one specific pair of values** is then 1/36. Here is a quick quiz: *What are the chances of getting 3 distinct pairs of dice rolls?*

The answer...... 3/36. This will be the case for any number, we simply **divide the number of specific pairs of dice rolls by 36, the total number of pairs we have**. We need to relate this back to our formal framework though.

### Formal Definition of Our Probability Measure
Remember, the elements of our event space are subsets of the sample space (including the whole sample space and the empty set). So we can state the intuition we learned above formally as:
$$
\begin{aligned}
&\hspace{3em}\mathcal{P}(E)=\frac{|E|}{|\Omega|},\text{ for }E\in\mathcal{F}\\
&\text{ where:}\\
&\hspace{1em}|E|=\text{ the number of elements in the set }E\\
&\hspace{1em}|\Omega|=36,\text{ the number of elements in our sample space}
\end{aligned}
$$
*Figure 3*
### Quick check of Axioms
If you are asking "what is an axiom?" don't worry. The "rules" in figure 4 are more formally known as "axioms". This is a philosophical topic in its own right, but the short version is: **A set of axioms is a set of logically consistent rules that we take as a given for the sake of definition.** The relation to what we are doing here: *we need to verify that our proposed probability measure shown in figure 4 adheres to the axioms (rules) of figure 14 from artilce 1
### Our Underlying Probability space
conclusion where we show our probability space tuple. This would be the measurable space associated with the left side of our random variable.