# Intro
Marcus Hutter and Jürgen Schmidhuber have been working on "universal artificial intelligence". A lot of people in artificial intelligence have been working on commercially viable products, from pagerank in search engines to expert systems for medical diagnosis. This is an applaudable field of work, but this will not bring us machines as smart as us any time soon. That is namely not the goal of these subfields of artificial intelligence. The field of "artificial general intelligence" however, has always been under a lot of critique. Probably because people do not like the endeavor at all. Maybe that can be seen as carnivores not liking scientific studies that seem to suggest that animals feel pain just like humans do... Anyway, credit must be given to scientists that go against the flow and try anyway!

# Concept
Let's talk about AIXI. If this is an acronym, I never found where it stands for. Maybe that's for itself to find out. It basically is very simple. It combines a "search strategy" over all possible futures of an agent (namely one using rewards), with a weight that favors parsimony (in the sense of the complexity of a program reaching this future, its sequence of actions and observations). 

# Equation
The equation is long, but contains a lot of repetitive elements:
<!--
http://latex.codecogs.com/gif.latex?a_k=\underset{a_k}{\mathrm{argmax}}\sum_{o_{k}r_k}\cdots\underset{a_m}{\mathrm{max}}\sum_{o_{m}r_m}[r_k+\cdots+r_m]\sum_{q=o_{1}r_1\cdots{o_{m}}r_m}2^{-l(q)}
-->
![equation](http://latex.codecogs.com/gif.latex?a_k%3D%5Cunderset%7Ba_k%7D%7B%5Cmathrm%7Bargmax%7D%7D%5Csum_%7Bo_%7Bk%7Dr_k%7D%5Ccdots%5Cunderset%7Ba_m%7D%7B%5Cmathrm%7Bmax%7D%7D%5Csum_%7Bo_%7Bm%7Dr_m%7D%5Br_k%2B%5Ccdots%2Br_m%5D%5Csum_%7Bq%3Do_%7B1%7Dr_1%5Ccdots%7Bo_%7Bm%7D%7Dr_m%7D2%5E%7B-L%28q%29%7D)

Several things have to be noted. The complexity measure originates from Solomonoff. Kolmogorov had been working at the same time on these problems and only found out later the work of Solomonoff. Anyhow, the complexity of a sequence is characterized by its Kolmogorov complexity "L". This sequence is a "program" that characterizes the machine as well as the environment. Solomonoff's insight was that it could be seen as a probability measure in the given form.

The reward has to be maximized over all future time steps, k to m, each delivering an additive element to the total reward. That sequence of actions is selected that leads to the maximum total reward (weighted with the complexity this sequence). Subsequently, the first action of this sequence of actions is returned as result. The next time step, the future is moved to "m+1" and everything repeats. 

# Thoughts
Some, preliminary thoughts on AIXI. Forgive me, I haven't had much time yet to think about it.

## Approximations to incomputable programs
The use of the Solomonoff complexity as a kind of universal prior is interesting. Okay, "L" might be incomputable and naturally a sum over incomputable measures, will be incomputable as well, but it makes sense that the objective can subsequently be an approximation. The only thing is, this doesn't seem like an "approximation" in the normal sense. Personally, I don't even know if it makes sense to talk about an approximation of an incomputable function. For that to exists, there must be certain asymptotic notions defined (recall the strong and weak law of large numbers for example).

## Non-additive rewards
More important to me, the formulation does not take into account that this is a limited machine. So, suppose we need these rewards for something... For example, the machine dies if these rewards do not come in at a minimum rate, just like food. A simple additive function that maximizes rewards over a long time period might lead to a strategy that postpones rewards till the total end, where extreme high rewards are predicted. The machine will starve itself and the extreme high rewards at the end will never be reached (assuming there is no robot heaven). Anyway, in so many words, the [r_k,...r_m] must be a function of the state of the robot. Of course it can't be set by the robot itself, or else the argmax becomes really easy for it ;-).

## Time
Due to the origins of this formulation, foremost Turing and Bellman, time plays a big role in this equation. A program is defined by its set of time-indexed trajectories over all possible perturbations and interactions with the real world. Although it first seems is that the "brute force" formulation of AIXI is expressive enough, this might not be the case. It might very well be argued that in the real world, there is not a finite set of reward-observation that can be summed over. What happens if the time step goes to zero for example? It also remains to be seen if Bellman's principle actually applies... To remind you: an optimal system when decomposed must necessarily exist out of optimal subsystems or the entire system wouldn't have been optimal to begin with. If the decomposition is over time, this leads to the commonly known separation principle of a Markovian blanket. This, naturally, does not hold for all systems (for an example of a non-Markovian optimal strategy, see [1]). Time as such as not used as an indexed quantity in dynamics systems [2].

## The universal calculator
Resource limitations for actually calculating AIXI or an approximation to AIXI are not take into account. Although often written in text, the typical recursive nature of Schmidhuber's work does not come to light here. The "universal calculator" does not seem to have to do calculations on how "feasible" its calculations are! This is at least not in the definition of AIXI. A more universal algorithm can hence be defined that also returns facts about feasibility or computability. Already in conventional optimal control the addition of resource constraints or the existence of stochasticity in the environment can make it optimal to delay a choice for a while [3]. For instance, only start to peddle when it is most convenient to you, e.g. when the current gets you close to either riverbank. What if in the more general setting it is not just about computational resource constraints, but about computability itself? This would mean we can actually not choose between L(q_1) and L(q_2)...

# References

1. When Bellman's Principle Fails [Piunovskiy]
2. Dynamic Systems vs. Optimal Control - a Unifying View [Schaal, Mohajerian, IJspeert]
3. An Introduction to Stochastic Control Theory, Path Integrals, and Reinforcement Learning [Kappen].

PS: These papers are selected because they can be found via scholar.google.com without library access, not because they have been published in fancy journals.
