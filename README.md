# Statistique-economie-et-gestion-avec-python
Analyse statistique des données economiques et financières avec python


Le tableau 1.8 contient un ensemble de données fournissant des informations sur 25 titres du marché secondaire listés par l’Association américaine des investisseurs individuels.

Les titres du marché secondaire sont souvent des titres de sociétés plus petites qui ne sont 

pas suivies de façon détaillée par les analystes de Wall Street. Les données sont disponibles en ligne dans le fichier Marché secondaire.

a) Combien de variables y a-t-il dans l’ensemble de données ?
b) Lesquelles sont qualitatives ? Lesquelles sont quantitatives ?
c) Pour la variable Place boursière, calculer la fréquence et la fréquence en pourcentage
    pour le marché AMEX, la bourse de New York et le marché OTC. Construire un
    graphique en barres similaire à celui présenté à la figure 1.5 pour la variable Place
    boursière.
d) Déterminer la distribution de fréquence pour la marge brute en utilisant cinq intervalles
    : 0-14,9 ; 15-29,9 ; 30-44,9 ; 45-59,9 ; 60-74,9. Construire un histogramme
    similaire à la figure 1.6.
e) Quel est le coefficient de capitalisation boursière moyen ?

#Importation des differentes librairies
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
#Importation du tableau 1.8
marche = pd.read_excel("Marché secondaire.xlsx")
marche
	Société 	Place boursière 	Symbole 	Capitalisation boursière (millions de dollars) 	Coefficient de capitalisation des résultats 	Marge brute (%)
0 	DeWolfe Companies 	AMEX 	DWL 	36.4 	8.4 	36.7
1 	North Coast Energy 	OTC 	NCEB 	52.5 	6.2 	59.3
2 	Hansen Natural Corp. 	OTC 	HANS 	41.1 	14.6 	44.8
3 	MarineMax, Inc. 	NYSE 	HZO 	111.5 	7.2 	23.8
4 	Nanometrics Incorporated 	OTC 	NANO 	228.6 	38.0 	53.3
5 	TeamStaff, Inc. 	OTC 	TSTF 	92.1 	33.5 	4.1
6 	Environmental Tectonics 	AMEX 	ETC 	51.1 	35.8 	35.9
7 	Measurement Specialties 	AMEX 	MSS 	101.8 	26.8 	37.6
8 	SEMCO Energy, Inc. 	NYSE 	SEN 	193.4 	18.7 	23.6
9 	Party City Corporation 	OTC 	PCTY 	97.2 	15.9 	36.4
10 	Embrex, Inc. 	OTC 	EMBX 	136.5 	18.9 	59.5
11 	Tech/Ops Sevcon, Inc. 	AMEX 	TO 	23.2 	20.7 	35.7
12 	ARCADIS NV 	OTC 	ARCAF 	173.4 	8.8 	9.6
13 	Qiao Xing Universal Tele. 	OTC 	XING 	64.3 	22.1 	30.8
14 	Energy West Incorporated 	OTC 	EWST 	29.1 	9.7 	16.3
15 	Barnwell Industries, Inc. 	AMEX 	BRN 	27.3 	7.4 	73.4
16 	Innodata Corporation 	OTC 	INOD 	66.1 	11.0 	29.6
17 	Medical Action Industries 	OTC 	MDCI 	137.1 	26.9 	30.6
18 	Instrumentarium Corp. 	OTC 	INMRY 	240.9 	3.6 	52.1
19 	Petroleum Development 	OTC 	PETD 	95.9 	6.1 	19.4
20 	Drexler Technology Corp. 	OTC 	DRXR 	233.6 	45.6 	53.6
21 	Gerber Childrenswear Inc. 	NYSE 	GCW 	126.9 	7.9 	25.8
22 	Gaiam, Inc. 	OTC 	GAIA 	295.5 	68.2 	60.7
23 	Artesian Resources Corp. 	OTC 	ARTNA 	62.8 	20.5 	45.5
24 	York Water Company 	OTC 	YORW 	92.2 	22.9 	74.2

#a) Combien de variables y a-t-il dans l’ensemble de données ?
marche.dtypes

Société                                            object
Place boursière                                    object
Symbole                                            object
Capitalisation boursière (millions de dollars)    float64
Coefficient de capitalisation des résultats       float64
Marge brute (%)                                   float64
dtype: object

#b) Lesquelles sont qualitatives ? Lesquelles sont quantitatives ?

société, place boursière symbole sont de type Qualitatif(Object)

Capitalisation boursière (millions de dollars) float64 Coefficient de capitalisation des résultats float64 Marge brute (%) float64 dtype: object sont de type Quantitatif(float64)

#c) Pour la variable Place boursière, calculer la fréquence et la fréquence en pourcentage
    pour le marché AMEX, la bourse de New York et le marché OTC. Construire un
    graphique en barres similaire à celui présenté à la figure 1.5 pour la variable Place
    boursière.
    
la fréquence et la fréquence en pourcentage de la variable Place boursière
effectif = marche['Place boursière'].value_counts()
effectif

Place boursière
OTC     17
AMEX     5
NYSE     3
Name: count, dtype: int64

modalites = effectif.index
modalites

Index(['OTC', 'AMEX', 'NYSE'], dtype='object', name='Place boursière')

frequence1 = pd.DataFrame(effectif)
frequence1
	count
Place boursière 	
OTC 	17
AMEX 	5
NYSE 	3
frequence1["n"] = effectif.values 
frequence1
	count 	n
Place boursière 		
OTC 	17 	17
AMEX 	5 	5
NYSE 	3 	3
#Calcul du frequence en pourcentage
frequence1["f"] = frequence1["n"] /  np.sum(frequence1["n"])*100
frequence1["f"]

Place boursière
OTC     68.0
AMEX    20.0
NYSE    12.0
Name: f, dtype: float64

f = pd.DataFrame(frequence1["f"])
f
	f
Place boursière 	
OTC 	68.0
AMEX 	20.0
NYSE 	12.0
Selection deleted
#Construire un graphique en barres similaire à celui présenté à la figure pour la variable Place boursière.
    
marche['Place boursière'].value_counts(normalize=True).plot(kind='pie')
plt.axis('equal')
plt.show()
Selection deleted
marche['Place boursière'].value_counts(normalize=True).plot(kind='bar')
plt.show()
