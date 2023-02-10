# Kullback-Leibler Divergence
___
[GitHub Link](https://github.com/janarw/kullback_leibler_divergence)

This is how I compute and analyse relative entropy, also known as Kullback-Leibler divergence (KLD), between US president's Inaugural Addresses in my Master's thesis.  
The foundation of the Bag of Words (BoW) class is from: [https://towardsdatascience.com/how-to-turn-text-into-features-478b57632e99](https://towardsdatascience.com/how-to-turn-text-into-features-478b57632e99)  
All further development is by Jana W.
# Corpus construction and vectorization
___
The corpus to be analysed consists of all US presiden'ts Inaugural Addresses from 1789 to 2021. Every speech, except the newest (Biden) speech were accessed via the nltk packages. The Biden speech was added manually. Each speech is vectorized into a one dimensional array. Then, the probability of each word is computed using Maximum Likelihood Estimation (MLE) of each word in the speech with respect to the overall vocabulary in the corpus and assigns each word a frequency value. To account for differences in vocabulary size, we use additive smoothing, also known as Laplace smoothing.
# Calculation of relative entropy
___
KLD between individual speeches is computed as follows:  

$D(P||Q)= \sum_{i}p(item_{i}|P)log_2\frac{p(item_{i}|P)}{p(item_{1}|Q)}$

Accordingly, a function was added.
#Visualisations
___
The evolution of KLD from oldest to newest Inaugural Address is displayed by a graph. Exemplarily see here under KLD between the first Inaugural Address, Washingon-1789, and all other speeches:
![example](https://github.com/janarw/kullback_leibler_divergence/blob/main/Images/Analyse_Teil1/kld_washington-all.png)  
Note that KLD is an asymmetrical measure and, thus, has different results for modelling P with Q and Q with P.  

Word clouds are used for visulatisation of the partcular words most responsible for KLD. For this, a fuction to compute pointwise KLD is added to the BoW class.  
In the python package Wordcloud, words are randomly coloured by default. With a modification of the colouring scheme we achieve definite colours depending on the pointwise KLD of the words. The colours are attributed as follows:  

pointwise KLD >$=$ 0.01 results in red, 0.008 $=$ orange, 0.006 $=$ green, 0.004 $=$ cyan, 0.002 $=$ blue, 0 $=$ purple.  

![example_wordcloud](https://github.com/janarw/kullback_leibler_divergence/blob/main/Images/Analyse_Teil2/wordcloud_kld(TEST).png)