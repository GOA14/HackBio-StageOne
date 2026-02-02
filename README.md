---

# TASK 1: GC Percentage Calculator

```r
gc_percent <- function(seq) {
  if (nchar(seq) == 0) {
    return(0)
  }

  s <- toupper(seq)
  bases <- unlist(strsplit(s, ""))
  gc_count <- sum(bases %in% c("G", "C"))
  (gc_count / length(bases)) * 100
}

gc_percent("GCATTTAT")
gc_percent("gcaTTTAT")

TASK 2: Protein Molecular Weight Calculator
protein_weight_kDa <- function(protein = "Grace") {

  aa_weights <- c(
    A = 89.09,  R = 174.20, N = 132.12, D = 133.10, C = 121.15,
    E = 147.13, Q = 146.15, G = 75.07,  H = 155.16, I = 131.18,
    L = 131.18, K = 146.19, M = 149.21, F = 165.19, P = 115.13,
    S = 105.09, T = 119.12, W = 204.23, Y = 181.19, V = 117.15
  )

  if (nchar(protein) == 0) {
    return(0)
  }

  protein <- toupper(protein)
  letters <- unlist(strsplit(protein, ""))

  if (any(!letters %in% names(aa_weights))) {
    return(0)
  }

  total_weight <- sum(aa_weights[letters])
  total_weight / 1000
}

protein_weight_kDa()
protein_weight_kDa("ACDE")
protein_weight_kDa("GRACE")
protein_weight_kDa("ACBDE")

Essay: Protein Molecular Weight Calculator
Introduction

To solve the protein molecular weight calculator task in R, I wrote a custom function (protein_weight_kDa()) that calculates the total molecular weight of a protein sequence based on the molecular weights of individual amino acids that were provided.

Defining the Function

First, I defined a function called (protein_weight_kDa()) and set my name, “Grace”, as the default input. This means that if no argument is provided when the function is called, the function automatically uses my name as the protein sequence.

Creating the Amino Acid Weight Table

Next, I created a named numeric vector called (aa_weights) to store the molecular weights of the standard amino acids. In this vector, each amino acid’s one-letter code is used as the name, and its molecular weight in Daltons is used as the value.

Handling Empty Inputs

Inside the function, I first checked whether the input protein sequence is empty. If the input has zero length, the function immediately returns 0.

Standardizing the Input Case

After checking for empty input, I converted the protein sequence to uppercase using the toupper() function. This ensures that the function works correctly even if the protein sequence is entered in lowercase or mixed case.

Splitting the Protein Sequence

To follow the hint provided, I split the protein sequence into individual amino acid elements using strsplit() and unlist().

Validating Amino Acids

I checked whether all amino acids exist in the amino acid weight table using the %in% operator. If any invalid amino acid is found, the function returns 0.

Calculating the Molecular Weight

If all amino acids are valid, I summed their molecular weights and converted the result from Daltons to kiloDaltons.
