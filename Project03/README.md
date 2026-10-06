# Introduction
In this project, we implemented a Gibbs sampling algorithm to discover DNA motifs from a collection of nucleotide sequences. Gibbs sampling is a probabilistic method that iteratively updates candidate motif positions based on how well they match a Position Weight Matrix (PWM) constructed from the other sequences.The algorithm begins by randomly selecting a k-mer from each sequence. During each iteration, one sequence is temporarily excluded, and the remaining candidate motifs are used to construct a Position Frequency Matrix (PFM) and Position Weight Matrix (PWM). The PWM is then used to score every possible k-mer in the excluded sequence. These scores are converted into probabilities, allowing the algorithm to probabilistically select a new motif position. Repeating this process allows the motif predictions to gradually converge toward a shared sequence pattern.This project demonstrates the use of Python, NumPy, probability-based sampling, PFMs, PWMs, and sequence analysis to solve a biological pattern-discovery problem. The resulting motif can also be visualized using a sequence logo to examine the nucleotide conservation at each position.

# Pseudocode
def GibbsMotifFinder (seqs, k, seed=None):
    '''
    Function to find a pfm from a list of strings using a Gibbs sampler
    
    Args: 
        seqs (str list): a list of sequences, not necessarily in same lengths
        k (int): the length of motif to find
        seed (int, default=None): seed for np.random

    Returns:
        pfm (numpy array): dimensions are 4xlength
    '''
    # Use rng to make random samples/selections/numbers
    # Example: randint = rng.integer(1, 10)
    random.seed(seed)
    rng = np.random.default_rng(seed)

    pass

```
GibbsMotifFinder(seqs, k, seed)

START with the input sequences (seqs) and motif length k

SET the random seed

CREATE an empty list called motifs
    # stores one motif for each sequence


INITIALIZE motifs:

    LOOP through each sequence in seqs:

        RANDOMLY select a valid k-mer position

        RANDOMLY select a strand (+ or -)

        IF the reverse strand is selected:
            GET the reverse complement of the k-mer

        ADD the selected k-mer to motifs


START convergence loop:

    REPEAT until motifs stop changing OR 10,000 iterations are reached:


        RANDOMLY select one sequence index i

        REMOVE motifs[i] temporarily from motifs


        BUILD a PFM using all motifs except motifs[i]

            USE build_pfm() from motif_ops.py


        BUILD a PWM from the PFM

            USE build_pwm() from motif_ops.py


        CREATE an empty list called candidates

            # stores possible k-mers, scores, and strand information


        LOOP through every possible k-mer position in seqs[i]:


            GET the forward k-mer

            GET the reverse complement of the k-mer

                USE reverse_complement() from seq_ops.py


            SCORE the forward k-mer using the PWM

                USE score_kmer() from motif_ops.py


            SCORE the reverse complement using the PWM

                USE score_kmer() from motif_ops.py


            STORE the k-mer, score, position, and strand
            in candidates


        CONVERT the candidate scores into probabilities


        RANDOMLY SAMPLE one candidate using the probabilities

            # higher scoring candidates have a higher chance
            # but do not select the maximum score directly


        GET the sampled k-mer and strand information


        UPDATE motifs[i] with the sampled motif


        CHECK if motifs have converged


BUILD the final PFM using all motifs

    USE build_pfm() from motif_ops.py


RETURN the final PFM

```

# Successes
Description of the team's learning points

# Struggles
Description of the stumbling blocks the team experienced

# Personal Reflections
## Group Leader
Group leader's reflection on the project

## Other member
Other members' reflections on the project

# Generative AI Appendix
As per the syllabus
