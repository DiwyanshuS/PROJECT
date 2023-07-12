SDS-1473

Objective: Q2 EGFR data to assign variant grouping to S768I, L861Q and G719X mutations.

Script: EGFR-S768I-L861Q-G719X-VariantGrouping.ipynb

This script read csv file containing EGFR molecular variant data and assign variant grouping to the following variants:

#EGFR variant representative from PT360 dataset

L861Q = ["p.L861Q", "c.2582T>A;p.L861Q", "c.2582T>A;p.L816Q",
        "L861Q", "c.2582T>A", "2582T>A", "p.Leu861Gln", "Leu861Gln"]

S768I = ["p.S768I", "c.2303G>T;p.S768I", "c.2303C>T;p.S768I", "c.2305G>T;p.S768I", "c.2303G>T","c.2303 G>T(p.S7681)", "_S768I_;p.Ser768IIe", "Exon  20 S7681",
"S768I", "c.2303G>T", "2303G>T", "p.Ser768Ile", "Ser768Ile" ]

G719X = ["p.G719A", "p.G719S", "p.G719C", "p.G719X", "G719X", "c.2156G>C;p.G719A", "p.G719D", "c.2155G>T;p.G719C","c.2155G>A;p.G719S", "p.G719", "c.2156G>C", "Exon 18 G719", "c.2154_2155delinsTT;p.G719C","Exon 18 G719X", "G719X 18", "G719", "c.2155G>A;p.G719X", "Codon G719", "c.2155G>C;p.G719A","c.2155G>T;p.G719X", "EXON 18 - G719X", "2155>T (G719X)", "c.2156G>C;p.G719X", "Exon 18| G719","c.2154_2156delinsTGC;p.G719A", "exon 18 (G719X)", "(mutations at codon G719 in exon 18", "exon 18   G719X","Exons 18 (G719X)", "Exons 19(G719X)", "p.G719K", "p.G719*"]

Note: Please replace your file in the pd.read_csv("your file.csv")