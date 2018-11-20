# DNAStrand-stuff-final-version-

# Name: Fuchun Yang
# Date: 10/3/2018

# This program is to read the DNAStrand and print out the complementary DNA as well as in reverse. 
# This part is to read the file that the user wants to open. 

name = input("Please enter the DNAStrand file that you want to test: ")
filename = name + ".txt"
fileLn = open(filename, "r")
line = fileLn.readline()
line = line.rstrip()
DNASequence = line
# This is to reset the 4 counts to 0. 
count_1=0
count_2=0
count_3=0
count_4=0
# This is for counting every letter and print how many As, Cs, Gs, Ts in the DNA sequence. 
for i in DNASequence:
    if i == "A":
        count_1 = count_1+1
    elif i == "T":
        count_2 = count_2+1
    elif i == "C":
        count_3 = count_3+1
    else:
        count_4 = count_4+1
print("There are",count_1,"'A's in the strand;",count_2,"'T's in the strand;",count_3,"'C's in the strand;",count_4,"'G's in the strand.")
# This is for reverse the matched DNA sequence and store it into the newWord. 
newDNA=" "
for i in DNASequence:
    if i == "A":
        Complementary = "T"
    elif i == "T":
        Complementary = "A"
    elif i == "C":
        Complementary = "G"
    else:
        Complementary = "C"
    newDNA = Complementary + newDNA
print("This is the complementary and reversed sequence:", newDNA)

fileName = "complement1.txt"
fileOut = open(fileName,"w")
fileOut.write(DNAComplement)
fileOut.close()

# reversedRNA = reversed RNA strand
# OriginalDNA = original DNA Strand
# This function works for transcribing the DNA sequence into matched RNA sequence and reverse the sequence.
def RNATranscribing(OriginalDNA):
    newRNA= " "
    for i in OriginalDNA:
        if i == "A":
            Complementary = "U"
        elif i == "T":
            Complementary = "A"
        elif i == "C":
            Complementary = "G"
        else:
            Complementary = "C"
        newRNA = Complementary + newRNA
    return newRNA
# This for loop is to keep asking the user to open the DNA and save the transcribed and reversed RNA sequence
for j in range(1,10000):
    i = input("Please enter which of the DNAStrand file that you want to transcribe: ")
    if i == "x":
        break
#This is for read the sequences in the files
    else:
        filename = "DNAStrand" + i + ".txt"
        fileIn = open(filename, "r")
        line = fileIn.readline()
        line = line.rstrip()
        DNAStrand = line
        fileIn.close()
#This is for calling the function and input the string "DNAStrand" into originalDNA and run the function
        transcribedRNA = RNATranscribing(DNAStrand)
#This is for writing the reversed and trascribed RNA sequence into a new document
        filename = "RNAStrand" + i + ".txt"
        fileOut = open(filename, "w")
        fileOut.write(transcribedRNA)
        fileOut.close()
