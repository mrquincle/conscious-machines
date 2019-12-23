# Modules & Interactions

There are several aspects to neural modules (with which are meant smaller populations of neurons that act together) and how they interact with each other. It is subdivided among the lines of:

* competition
* synchronization 

## Competition 

Competition between different neural modules is a reoccurring theme within many neurorobotic approaches. The normal computer science term of one of these competition schemes is a so-called [winner-take-all](https://en.wikipedia.org/wiki/Winner-take-all) [WTA] network. As soon as their is some feedback mechanism in place that allows output neurons to inhibit each other, while activating themselves, it is actually almost impossible not to have a winning neuron (due to minute fluctuations or timing peculiarities one of them will be positively reinforced). In computer vision a well-known processing step is so-called [non-maximum suppression](https://en.wikipedia.org/wiki/Canny_edge_detector#Non-maximum_suppression). Noise gets removed, and local winners emerge (often "edges" in this context of image processing). In general machine learning this phenomenon will be called mode seeking: pinpointing the maximum of a probability density function. One of the most well-known methods of mode seeking is the [mean-shift](https://en.wikipedia.org/wiki/Mean-shift) procedure.

### Subsumption

The oldest theory and most widely used in robotics is the [subsumption architecture](https://en.wikipedia.org/wiki/Subsumption_architecture) from Brooks. This assigns an OSI-like model to control layers in the brain. Neatly defined tasks are able to overrule tasks that are defined on a lower level. In this architecture there is no competition. A task such as "wandering around" is implemented once, and there are not five other tasks competing for the same resources. No, they are neatly stacked in a functional hierarchy and competition through intricate inhibition and subsumption schemes does not seem to have had large priority in the community.

### Workspaces

With neuroscientific theories I have encountered the [global workspace theory](https://en.wikipedia.org/wiki/Global_Workspace_Theory) by Baars. The brain is a stage and different modules enter this stage in a competitive fashion. This is like a WTA network, but it requires also a mechanism to get a module **off** the stage. The mechanistic aspects are incorporated in an actual computer architecture by Franklin, in [(L)IDA](https://en.wikipedia.org/wiki/Artificial_consciousness#Franklin.E2.80.99s_Intelligent_Distribution_Agent). IDA makes use of codelets, one lesser known invention by Hofstadter (yes, the guy from GEB). The WTA network is called a slipnet and the reference design is [Copycat](https://en.wikipedia.org/wiki/Copycat_(software)). A slipnet typically exists of semantically meaningful nodes (rather than neurons) and semantically meaningful edges (such as "opposite" or "left of"). I haven't checked the details, but activation seems indeed to follow some [RC](https://en.wikipedia.org/wiki/RC_circuit) curve. And learning is through a Hebbian-like mechanism.

### Natural selection

Edelman just basically applies the principle of natural selection to groups of neurons. The groups that are used often, will stay in existence. The parallel quickly fails of course, but might be helpful. I don't think however that many people see certain chemical compounds as predators in the world of the brain. In evolution momentarily the idea of group selection was posed. Mass assembly events can be used for a specie to count its members and for example to reduce the effects of densities that become too high, an individual can be (unconsciously) be inclined to get less offspring. The thing however breaks down when thinking what this means on the level of the individual gene. A gene reducing reproduction of the individual is its own demise. Without a genetic representation, natural selection of the level of neurons, is an impoverished metaphor, where these types of consequences of possible selection mechanisms cannot be thought through.

### Loops

Sensorimotor loops, and especially, cross-coupled perception loops are required according to Haikonen [1]. This fulfills the role of sensor fusion, integrating the information from different modalities. He also postulates that non-sensory information is feed into this system in the same manner. Emotions however seem to be fed into it through a different "modulating" pathway. The total absence of how things are actually implemented in the brain is a pity and makes it hard as an engineer to just trust him and build it like this. It is however extremely similar to [Wolpert](https://www.ted.com/talks/daniel_wolpert_the_real_reason_for_brains)'s loops. These are common [sensorimotor loops](https://en.wikipedia.org/wiki/Sensory-motor_coupling) that run in parallel. This technology uses a bit more of modern machine learning, notably gradient descent and expectation-maximization.

### Polychronous groups

A very interesting phenomenon in networks with variable delays are so-called [polychronous groups](http://www.izhikevich.org/publications/spnet.htm) by Izhikevich. In such a network groups can be identified that do not fire together, but do fire consistently in a group with fixed intermediate delays. Due to synchronization at arrival time, a consistent firing **pattern** can be exhibited by a group of neurons.

### Virtual machine

Shananan heavily borrows from global workspace theory and adds an interesting twist. The WTA network can be seen he states [2] as a virtual machine implemented on massively parallel hardware. The states however are different than in the normal von Neumann architecture, they are much richer, exhibiting internal dynamics. What is similar to the virtual machine is that there is an entity, the **connective core**, that is a kind of processing bottleneck, something that serializes the data, allowing suddenly syntactic and logical constructions such as chaining events or manipulating sequences.

![The connective core](http://rstb.royalsocietypublishing.org/content/367/1603/2704/F3.large.jpg)

Still there is something smelly about these constructions, as with the genotype-phenotype level of selection. In case the dynamic WTA network leads to a (cognitive) pattern that makes sense, than the competition in the individual "stages", the subsequent winners, are not real competitors, but collaborators if seen over time.

## Synchronization

The negative formulation of how to implement synchronization between neural modules is the "binding problem". 

### Cross-frequency coupling

Franklin et al. [3] propose coupling between high and low frequency EEG bands as the way the brain integrates information. Objects in the environment are coupled to low-energy perceptual oscillators. Why these need to be oscillators and other static/dynamic representations are not sufficient is not clear though. Cognitive concepts are represented by high-frequency gamma assemblies and organized within low-frequency theta response patterns. It is shown that the amplitude of the gamma oscillations is modulated by the theta rhythms. And theta rhythms are correlated with sniffing and whisking sensory intake.

Gamma activity between a low-level visual neuron (say a horizontal edge detection unit), and a high-level visual neuron (say a face detection unit), can cause a stronger reaction from the low-level neuron, than in the case there is no corresponding high-level representation. Likewise words induce higher gamma activity than pseudo-words. This is called the **match and utilization model**. Summarized, gamma oscillations are widely recognized as having functional importance. However, above scenarios are related to sensory input. As soon as higher association areas come into play, such as the hippocampus, working memory, etc. slower frequency become important (see Basar et al. [4]), like the mentioned theta waves, but also alpha waves. 

Very interesting, gamma activity is coupled to pathological conditions, from ADHD to Schizophrenia [5]. Personally I find it unlikely that it would explain so many cognitive disorders, but it is interesting to see that there is such a strong connection between dopamine and gamma activity: more dopamine, than more gamma activity. Increased gamma activity in sensory parts lead to déjà vu effects. Increased gamma activity in memory parts lead to hallucinations.

The question is: why using frequency bands for coordination? And do we have methods to store information in (loosely) coupled oscillators?

[ to do ]

## Some thoughts...

It is remarkable that actually the nature of the information exchanged between the modules, or the dynamics exhibited through the interactions between the modules, is not scrutinized in the above architectures. It is obvious that not every designed WTA network will be conscious. The type of information that has to be exchanged is of utmost importance, such as:

* information about history (autobiographic details), information about emotional states, information about geographic and spatial state
* information about mental states, information about someone's own character
* information about sensory input, information about body posture

It seems reasonable to suggest that the complexity with which we can handle information about ourselves on higher abstraction levels than other animals, must be reflected in the variety and granularity with which self-* type information is handled throughout our brain. These are recent evolutionary inventions and our vocabulary is not yet up to date to describe them (e.g. pain vs nociception).

As an engineer and computer scientist I see directly how tempting it is to start postulating modules and functional layers. However, this cannot be the right approach if we are talking about a highly interwoven system. It makes more sense to come up with clustering methods that extract in an unsupervised manner the behaviour exhibited by the system (say walking) combined with its internal state (say a [central pattern generator](https://en.wikipedia.org/wiki/Central_pattern_generator)). For this to work, we only have to do one thing. Design EEG sensors, such as the one from [Emotiv](http://emotiv.com/), but with much higher resolution and penetration capabilities, have it **on all the time**, and **record** all activities you perform, things you see, and things you say.

[1] Artificial Minds and Conscious Machines, Haikonen

[2] The Brain's Connective Core and its Role in Animal Cognition ([html](http://rstb.royalsocietypublishing.org/content/367/1603/2704/F3.expansion.html)), Shanahan

[3] Global Workspace Theory, its LIDA model and the Underlying Neuroscience, Franklin

[4] Gamma, Alpha, Delta, and Theta Oscillations Govern Cognitive Processes, Basar et al.

[5] Human EEG gamma oscillations in neuropsychiatric disorders (2005), Herrmann, Demiralp
