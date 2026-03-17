# -----------------------------------------------------------------------------
# 🐍 Ep 1 - Pattern Count
# Find how many times a given pattern (motif) occurs in a DNA sequence
# -----------------------------------------------------------------------------

def PatternCount(Text, Pattern):
    """
    Counts the number of times a Pattern appears in a DNA Text sequence.

    Args:
        Text    (str): The parent DNA sequence.
        Pattern (str): The motif/pattern to search for.

    Returns:
        int: Number of occurrences of Pattern in Text.
    """
    count = 0
    for i in range(len(Text) - len(Pattern) + 1):
        if Text[i:i+len(Pattern)] == Pattern:
            count += 1
    return count


# Example usage - Ep 1
text    = 'ATGCATATGACTACTAGATACTGATACTGATACATA'
pattern = 'ATA'
print("=" * 50)
print("🐍 Ep 1 - Pattern Count")
print(f"   Sequence : {text}")
print(f"   Pattern  : {pattern}")
print(f"   Count    : {PatternCount(text, pattern)}")  # Output: 5
print()


# -----------------------------------------------------------------------------
# 🐍 Ep 2 - Frequency Map
# Build a dictionary mapping each k-mer to its occurrence count
# -----------------------------------------------------------------------------

def FrequencyMap(Text, k):
    """
    Builds a frequency map of all k-mers in a DNA sequence.

    Args:
        Text (str): The DNA sequence.
        k   (int): Length of the k-mer.

    Returns:
        dict: A dictionary mapping each k-mer to its frequency count.
    """
    freq = {}
    n = len(Text)
    for i in range(n - k + 1):
        Pattern = Text[i:i+k]
        freq[Pattern] = freq.get(Pattern, 0) + 1
    return freq


# Example usage - Ep 2
text = 'ACGTTGCATGTCGCATGAGCATGAGAGCT'
k    = 3
print("=" * 50)
print("🐍 Ep 2 - Frequency Map")
print(f"   Sequence : {text}")
print(f"   k-mer length : {k}")
print(f"   Frequency Map : {FrequencyMap(text, k)}")
print()


# -----------------------------------------------------------------------------
# 🐍 Ep 3 - Most Frequent K-mers
# Identify the k-mers that appear most frequently in the sequence
# -----------------------------------------------------------------------------

def FrequentWords(Text, k):
    """
    Finds the most frequent k-mers in a DNA sequence.

    Args:
        Text (str): The DNA sequence.
        k   (int): Length of the k-mer.

    Returns:
        list: A list of k-mers with the highest frequency.
    """
    freq  = FrequencyMap(Text, k)
    m     = max(freq.values())
    return [key for key in freq if freq[key] == m]


# Example usage - Ep 3
Text = 'ACGTTGCATGTCGCATGAGCATGAGAGCT'
k    = 3
print("=" * 50)
print("🐍 Ep 3 - Most Frequent K-mers")
print(f"   Sequence      : {Text}")
print(f"   k-mer length  : {k}")
print(f"   Most Frequent : {FrequentWords(Text, k)}")  # Output: ['GCA', 'CAT', 'ATG']
print()


# -----------------------------------------------------------------------------
# 🐍 Ep 4 - Complementary DNA String
# Generate the complementary strand of a DNA sequence (A↔T, C↔G)
# -----------------------------------------------------------------------------

def Complement(Pattern):
    """
    Returns the complementary DNA strand of a given sequence.

    Complement rules:
        A  <->  T
        C  <->  G

    Args:
        Pattern (str): A DNA sequence string.

    Returns:
        str: The complementary DNA sequence.
    """
    mapping = {'A': 'T', 'T': 'A', 'C': 'G', 'G': 'C'}
    return ''.join(mapping[base] for base in Pattern)


# Example usage - Ep 4
sequence = 'ACGTTGCATGTCGCATGAGCATGAGAGCT'
print("=" * 50)
print("🐍 Ep 4 - Complementary DNA String")
print(f"   Original    : {sequence}")
print(f"   Complement  : {Complement(sequence)}")  # Output: TGCAACGTACAGCGTACTCGTACTCTCGA
print()


# -----------------------------------------------------------------------------
# 🐍 Ep 5 - Pattern Matching in DNA Sequence
# Find all starting positions where a pattern occurs in a genome sequence
# -----------------------------------------------------------------------------

def PatternMatching(Pattern, Genome):
    """
    Finds all starting positions of a Pattern within a Genome sequence.

    Args:
        Pattern (str): The DNA motif to search for.
        Genome  (str): The full genome/DNA sequence to search in.

    Returns:
        list: A list of starting indices where Pattern is found in Genome.
    """
    Positions = []
    for i in range(len(Genome) - len(Pattern) + 1):
        if Genome[i:i+len(Pattern)] == Pattern:
            Positions.append(i)
    return Positions


# Example usage - Ep 5
genome  = 'CGCGATACGTTACATACATGATAGACCGCGCGCGATCATATCGCGATTATC'
pattern = 'CGCG'
print("=" * 50)
print("🐍 Ep 5 - Pattern Matching")
print(f"   Genome   : {genome}")
print(f"   Pattern  : {pattern}")
print(f"   Positions: {PatternMatching(pattern, genome)}")  # Output: [0, 16, 28, 38]
print()

print("=" * 50)
print("✅ All episodes executed successfully.")
print("=" * 50)
