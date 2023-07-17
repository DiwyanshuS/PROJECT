SDS-1473

Objective: Q2 MET NSCLC data to assign variant grouping to MET exon 14 skipping mutations.

Script: MET-Exon-14-Skipping-Mutation-VariantGrouping-v1.0.ipynb

This script read csv file containing MET molecular variant data and assign variant grouping to the following variants:

keyword1 = 'MET exon 14 skipping'
keyword2 = 'MET exon 14 skipping mutation'

variant_patterns = [
    'c.3028G>C', 'c.288-15_2892del20', 'c.2888-10_2911del34', 'c.2888-10C>G',
    'c.2888-12_2888-4delCTCTGTTTT','c.2888-12_2909del','c.2888-14_2888-4del',
    'c.2888-14_2888-4delCTCTCTGTTTT','c.2888-14_2895del22','c.2888-15_2888-2del14',
    'c.2888-15_2888-3del','c.2888-15_2888-4del','c.2888-15_2888-4delTCTCTCTGTTTT',
    'c.2888-15_2890delTCTCTCTGTTTTAAGATC','c.2888-16_2888-4del','c.2888-16_2891del',
    'c.2888-16_2891del;p.D963fs','c.2888-16_2896del25','c.2888-17_2888-16insAGAA',
    'c.2888-17_2888-1del','c.2888-17_2905delTTTCTCTCTGTTTTAAGATCTGGGCAGTGAATTAG',
    'c.2888-18_2888-3del','c.2888-18_2888-9delCTTTCTCTCT','c.2888-19_2888-3del',
    'c.2888-19_2888del','c.2888-19>2888-2delCTTTCTCTCTGTTTTAA','c.2888-1G>A',
    'c.2888-2_2915del','c.2888-20_2888-11del','c.2888-20_2888-11delTTCTTTCTCT',
    'c.2888-20_2888-1del','c.2888-20_2888-7>C','c.2888-20_2939del','c.2888-21_2888-5del',
    'c.2888-22_2888-2del','c.2888-22_2891del','c.2888-22_2891del;p.D963fs','c.2888-24_2888-10del15',
    'c.2888-25_2888-3>ACT','c.2888-27_2888-12del','c.2888-28_2888-14del','c.2888-28_2888-3>TTAG',
    'c.2888-28_2888-9del20','c.2888-28_2891>G','c.2888-29_2888-2delACAAGCTCTTTCTTTCTCTCTGTTTTAA',
    'c.2888-30_2888-15del16','c.2888-30_2888-2del29','c.2888-30_2888-3del28','c.2888-30_2888-9del22',
    'c.2888-33_2888-1del','c.2888-35_2888-17del','c.2888-35_2888del','c.2888-36_2888-12del25',
    'c.2888-4_2907del','c.2888-4_2907del;p.D963fs','c.2888-40_2888-17del24',
    'c.2888-40_2888-20delAGCCGTCTTTAACAAGCTCTT','c.2888-40_2888-23del18','c.2888-47_2888-24del24',
    'c.2888-5_2890TTAAGATC>A','c.2888-5_2904del22','c.2888-5_2905>AA','c.2888-5_2944del62',
    'c.2888-52_2888-1del','c.2888-61_2888-12>27','c.2888-7_2920del','c.2888A>G','c.2888A>G;p.D963G',
    'c.2903_3028+67del','c.2905_2940del','c.2942-10_2958del27','c.2942-14_2942-3del',
    'c.2942-14_2942-4del','c.2942-14_2945del','c.2942-15_2942-4del12','c.2942-15_2943del',
    'c.2942-15_2946del20','c.2942-16_2942-15insAG','c.2942-16_2946delTTCTCTCTGTTTTAAGATCTG',
    'c.2942-17_2942-14delinsAGAAA','c.2942-18_2942-5del ','c.2942-18_2942-6del','c.2942-18_2942-7del12',
    'c.2942-18_2942-8del ','c.2942-19_2942-13delinsA','c.2942-20_2945del24','c.2942-20_294del26',
    'c.2942-21_2942--17delinsGAAA','c.2942-27_2964del','c.2942-28_2942-10del19','c.2942-31_2942-4del',
    'c.2942-3A>G','c.2942-40_2942-20del','c.2942-42_2946del47','c.2942-47_2949del','c.2994_3028+1del',
    'c.3001_3021delGTAGACTACCGAGCTACTTTT;p.V1001_F1007del',
    'c.3003_3028+1delAGACTACCGAGCTACTTTTCCAGAAGGinsCTGTAGCTGCT','c.3007T>C','c.3007T>C;p.Y1003H',
    'c.3008A>G;p.Y1003C','c.3010_3028+8del','c.3012_3028+6del','c.3017_3028+3del15',
    'c.3017_3028+5del17','c.3017_3028+del27','c.3017_3028delCTTTTCCAGAAGGT','c.3018_3028+13del',
    'c.3018_3028+14del','c.3018_3028+14del;p.F1007fs','c.3018_3028+8del','c.3018_3028+del',
    'c.3020_3028+24del','c.3021_3028+14del22','c.3021_3028+2delTCCAGAAGGT','c.3024_3028delAGAAGGTATATT',
    'c.3025_3027GAA>Gfs','c.3025_3028+13del17','c.3026_3028+5delAAGGTATA','c.3027_3028+13del',
    'c.3027_3028+13del;p.D1010fs','c.3027_3028+1delAGG','c.3027_3028+2delAGGTA','c.3027_3028delAG',
    'c.3027_3028delAG;p.D1010fs*4','c.3027_3028ins','c.3028_3028+3delGGTA','c.3028+1_3028+25del25',
    'c.3028+1_3028+2GT>AA','c.3028+1_3028+3GTA>CTT','c.3028+1_3028+9del','c.3028+1G>A','c.3028+1G>C',
    'c.3028+1G>T','c.3028+2_3028+10delTATATTTCA','c.3028+2_3028+4del','c.3028+2T>A','c.3028+2T>C',
    'c.3028+2T>G','c.3028+3_3028+7del','c.3028+3_3028+7delATATT','c.3028+3A>G','c.3028+3A>T',
    'c.3028G>A','c.3028G>A;p.D1010N','c.3028G>C','c.3028G>C;p.D1010H','c.3028G>T',
    'c.3028G>T;p.D1010Y','c.3029C>T','c.3029C>T;p.T1010I','c.3058_3082+8delinsATA',
    'c.3067_3082+1delinsC','c.3069_3081del','c.3073_3082+2del','c.3073_3082+4del14',
    'c.3076_3082+17del','c.3076_3082+2del','c.3076_3082+3del10','c.3077_3082+9delCAGAAGGTATATTTC',
    'c.3081_3082+3del','c.3082_3082+1del','c.3082+1_3082+13del13','c.3082+1delG','c.3082+1G>A',
    'c.3082+1G>C','c.3082+1G>T','c.3082+2_3082+9del','c.3082+2T>A','c.3082+2T>C',
    'c.3082+3A>G','c.3082+3A>T','c.3082+6T>G','c.3082C>G','c.3082C>G;p.L1028V','c.3082del',
    'c.3082G>A','c.3082G>A;p.D1028N','c.3082G>C','c.3082G>C;p.D1028H','c.3082G>T',
    'c.3082G>T;p.D1028Y','c.3208G>C','c.3208G>C;p.D1010H','c.3280C>T;p.H1094Y',
    'p.D1010fs','p.D1010fs*4','p.D1010H','p.D1010N','p.D1010Y','p.D1028H','p.D1028N','p.D1028Y',
    'p.D963fs','p.D963G','p.F1007fs','p.L1028V','p.T1010I','p.Y1003H'
]

#these variant patterns are extracted from gn360 dataset and few literatures

Note: Please replace your file in the pd.read_csv("your file.csv")