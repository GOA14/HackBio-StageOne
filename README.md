#TASK 1
gc_percent <- function(seq) {          # Create a function called gc_percent with input 'seq'
  if (nchar(seq) == 0) {                # Check if the input sequence is empty
    return(0)                           # If empty, return 0 to avoid division by zero
  }
s <- toupper(seq)                     # Convert all letters in the sequence to uppercase
bases <- unlist(strsplit(s, ""))      # Split the sequence into individual letters
gc_count <- sum(bases %in% c("G", "C"))# Count how many letters are G or C
(gc_count / length(bases)) * 100      # Calculate and return GC percentage
}
gc_percent("GCATTTAT")                  # Test the function using uppercase input
gc_percent("gcaTTTAT")                  # Test the function using mixed-case input

#Task 2
# Test examples
protein_weight_kDa()            # Uses default name "Grace"
protein_weight_kDa("ACDE")      # Multiple amino acids (split into a vector and looked up)
protein_weight_kDa("GRACE")     # Valid protein sequence
protein_weight_kDa("ACBDE")     # Contains invalid amino acid -> returns 0

#Write an essay describing the step-by-step recipe with which you solved the (protein weight calculator) task in R
#INTRODUCTION

To solve the protein molecular weight calculator task in R, I wrote a custom function (protein\_weight\_kDa()) that calculates the total molecular weight of a protein sequence based on the molecular weights of individual amino acids that were provided.

#DEFINING THE FUNCTION

First, I defined a function called (protein\_weight\_kDa()) and set my name, “Grace”, as the default input. This means that if no argument is provided when the function is called, the function automatically uses my name as the protein sequence.

#Creating the Amino Acid Weight Table

Next, I created a named numeric vector called (aa\_weights) to store the molecular weights of the standard amino acids. In this vector, each amino acid’s one-letter code is used as the name, and its molecular weight in Daltons is used as the value. This structure allows for easy lookup of amino acid weights during the calculation.

#HANDLING EMPTY INPUTS

Inside the function, I first checked whether the input protein sequence is empty. If the input has zero length, the function immediately returns 0. This step prevents errors and ensures that the function behaves correctly when no sequence is provided.

#STANDARDIZING THE INPUT CASE

After checking for empty input, I converted the protein sequence to uppercase using the toupper() function. This ensures that the function works correctly even if the protein sequence is entered in lowercase or mixed case.

#SPLITTING THE PROTEIN SEQUENCE

To follow the hint provided, I then broke the protein sequence into individual amino acid elements. I used the strsplit() function to split the string into single letters and unlist() to convert the result into a vector. Each element of this vector represents one amino acid in the protein sequence.

#VALIDATING AMINO ACIDS

I then checked whether all the amino acids in the vector exist in the amino acid weight table. This was done using the %in% operator. If any character is not a valid standard amino acid (for example, “B”), the function immediately returns 0, as required by the task.

#CALCULATING THE MOLECULAR WEIGHT

If all amino acids are valid, I calculated the total molecular weight by looking up each amino acid’s weight from the named vector and summing the values. Finally, I converted the total molecular weight from Daltons to kiloDaltons by dividing the result by 1000 and returned the final value.
