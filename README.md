# blastABIN


BLAST
Algorithms for Bioinformatics 2020

Team:
Chhavi Munjal     2018387
Sejal  Singhal       2018413
Shreeya Garg       2018415
Vrinda Singhal     2018421

Aim:   
Python implementation of the Basic Local Alignment Search Tool (BLAST). A BLAST search enables a researcher to compare a query sequence with a library or database of sequence and identify library sequences that resemble the query sequence above a certain threshold.

IMPLEMENTATION:

Input:
 2 fasta files: 
	Query: ex2.fasta (Attenuated influenza virus)
	Subject: ex.fasta (Severe acute respiratory syndrome coronavirus 2 isolate Wuhan-Hu-1, complete genome)
The user is given a choice to upload either a fasta file or directly input the sequence  strings

Algorithm:
      
Subject seq words: Finding all the l-mers of the subject  DNA sequence and hashing their key with the starting position. Keys are numerical encoding of the l-mer. 
	L-mer length: 11 
HSSP Score: 8 ( Essentially means we are tolerating up to  mutations while seeding) 

Query Words: Finding all the l-mers and their mutation with ( with score > HSSP Score ) of the given query strings. These are hashed to the starting position

Seeding: Finding matches between sequence words and HSSP from the query string 

Extension:  Extending the seeded matches using Smith-Waterman Algorithm (ungapped)
	Scoring Scheme: + 1 for a match, -1 for a mismatch
Extension Threshold: 6 ( If the score drops below this threshold while extension    we stop extending, dependent on our initial HSSP score )

Significance: Constants lambda and K are calculated for Karlin Atschul equation. These constants are dependent on the probability of nucleotide in query and DNA sequence and the scoring scheme. These constants are used to evaluate the E value and probability. 
E = Kmne^(−λS), where 
→ k and λ are Karlin Atschuk constants. 
→ m is the size of the query strings 
→ n is the size of the subject stings
→ S is the raw score of the alignment
E-Values Threshold: 0.005
Probability( T > S)  = probability of finding an alignment with score T greater than our score of S.

Salient Features:
Hashing is used to optimize the search complexity 
L-mers are encoded in numerical representation 
The results are displayed in GUI application for better understanding.
Plots are made for better visualization of the results
The results are compared and analyzed with the results obtained from the BLAST web server

Screenshot of the application:




Study 1 ( Influenza : COVID ) :
Input Query Sequence: Query.fasta (Attenuated influenza virus genome)
Input Subject Sequence: Subject_Seq.fasta (Severe acute respiratory syndrome coronavirus 2 isolate Wuhan-Hu-1, complete genome)
Results of BLAST web server-:
Parameters:
Expect threshold=0.005
Word size =11
HSSP score =8
Match/Mismatch scores= 1,-1
Results obtained through Blast web-server :
Maximum Score = 42.1
Total score = 378
Query cover =36%
E-value =9e-07
Number of Hits:9
Distribution of top 9 Blast Hits on 1 subject sequence



We used the query sequence and extracted the top 9 hits on the subject sequence given as input. Maximum hits were found at the starting position of 85-120 and 130-170 within the query sequence.
1. First hit: Query sequence - from position 85 to 117
	       Subject sequence-from position 29903 to 29871 

2. First hit:Query sequence - from position 86 to 118
       Subject sequence-from position 29903 to 29871 

3. First hit:Query sequence - from position 87 to 119
       Subject sequence-from position 29903 to 29871 

4. First hit:Query sequence - from position 88 to 120
      Subject sequence-from position 29903 to 29871 

5. First hit:Query sequence - from position 89 to 121
       Subject sequence-from position 29903 to 29871 

6. First hit:Query sequence - from position 90 to 122
       Subject sequence-from position 29903 to 29871 

7. First hit:Query sequence - from position 91 to 123
        Subject sequence-from position 29903 to 29871 

8. First hit:Query sequence - from position 92 to 124
       Subject sequence-from position 29903 to 29871 

9. First hit:Query sequence - from position 135 to 167
        Subject sequence-from position 29903 to 29871 

Dot plot: Showing the matched regions in Query and Subject sequence 

Results Obtained From our BLAST Implementation-:
 Then we got the following result-:
Number of Hits: 4
Maximum Query cover: 51.6%
Best E-value obtained=1.86e-05
Best Score: 26
OUTPUT:


Time is taken by our algorithm to implement-:
Time Required:  13.022059679031372  s
Comparing the results of study 1 :
Similar results are obtained with both the algorithms. 
The Blast web-server shows that hits are predominant at the query starting position from 85 to 120
Through our algorithm, we obtained most of our hits in the similar region.
Blast web-server results showed that alignment is mostly present due to “T”. For example:

Similar results are obtained through our algorithm. For example :
  Ou
Comparison of our Implementation with BLAST Web Server Implementation:
We got best Query coverage as 51.6% in our implementation while BLAST webserver got best Query coverage as 36%.
We got the best E-Value as 1.86e-05 while the best E-Value observed by the BLAST web server is 9e-07.
The best-matched alignment had a score of 26.59 in our algorithm while BLAST server gave the best score as 42.1. 
BLAST web server identified 9 hits while our server identified 4 hits between the query string and sequence string 
Study 2:
Query Sequence-: ex3.fasta (HIV virus)
Subject Sequence-: ex.fasta (Severe acute respiratory syndrome coronavirus 2 isolate Wuhan-Hu-1, complete genome)
BLAST web server showed 0 hits for the above two sequences using the same parameters as above.
OUTPUT-:
 When we ran the two sequences for our Implementation of BLAST with the same parameters as above then we get 0 hits too. 
Output-:
So we observe that we get similar results while comparing HIV virus with coronavirus through BLAST web server and through our implementation of BLAST.
Observations: 
Coronavirus Wuhan genome shows similarity with Influenza virus but it doesn't not show any similarity with HIV virus. 
References: 
 [ 1 ] Methods for Assessing the Statistical Significance of Molecular Sequence Features by Using General Scoring Schemes. Samuel Karlin and Altschul 1990
[ 2 ] Basic Local Alignment Search Tool Stephen F. AltschuP, Warren Gish ~, Webb Miller 2 Eugene W. Myers


