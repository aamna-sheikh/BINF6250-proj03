# Introduction
Description of the project

# Pseudocode
Put pseudocode in this box:

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
