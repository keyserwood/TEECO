<style type = "text/css">@page {size:letter;margin:-1em -3.5em -1em;text-align: justify;}//theme = academic & px = 12</style>

Elouan RAYMOND

# Projet personnel - TEECO 

****

## Partie 1 : Le mix électrique français en 2019

> ###### Question 1 : L'origine des données 
>
> *Toutes les données nécessaires sont disponibles gratuitement en ligne. Voici quelques sites utiles :*
> 	https://opendata.reseaux-energies.fr/pages/accueil/
> 	https://bilan-electrique-2019.rte-france.com/
> 	https://transparency.entsoe.eu/
>
> *Qui fournit les donnés disponibles sur ces sites ? Pourquoi ?* 

 La loi  pour une république numérique du 7 octobre 2016 (ou loi Lemaire) prévoit entre autre l'accès aux données publiques. L'Etat, les collectivités, les personnes de droit public ou de droit privés chargées d'une mission de service public doivent fournir des données. De nombreuses base de données sont ainsi accessible, comme le registre Sirene des entreprises, mais aussi les données liée à l'energie. 

De nombreux acteurs de l'énergie public ou privés ont mis à disposition des données (hors données personnelles). EDF a mis en ligne les données propres à ses infrastructures, sa production et la consommation en Corse et en outre-mer. Enedis et RTE qui gèrent le réseau de distributrion mettent en ligne les quantités d'électricité consommées et produits sur toute la France. GRTgaz et Teréga ont créé la plateforme opendata réseaux qui regroupe des acteurs privés afin d'allier données energétiques et données climatiques. Un accès et une mutualisation de ces données permet une meilleure comprhénsion du système et de meilleures prises de décisions, notamment grâce à des analyses intersectorielles.

> **Question 2 :** Pour l’année 2019 uniquement, présenter les indicateurs clés permettant de comprendre
> le mix électrique français (côté demande et côté offre).

RTE réalise un bilan à la fin de chaque année pour faire un tour d'horizon de la production et de la consommation d'électricité dans le pays. 

*La synthèse s'articule autour de 5 grands axes  :* 

| Axe d'analyse                                | Indicateurs clés                                             | Valeurs pour 2019                                            |
| -------------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 1. **Production d'électricité**              | - Production totale d'électricité [TWh] et et évolution par rapport à l'année précédente [%]<br>- Part de chaque sources de production (nuclaire, hydraulique, éolien ...) [TWh] | -537.7 TWh produit (-2%)<br><br>Nucléaire(70.2%)\|Renouvelables(21.4%) |
| **2. Consommation**                          | - Consommation totale d'électricité [TWh] et évolution par rapport à l'année précédente [%] | - 473TWh consommé (-0.5%)                                    |
| **3. Echanges d'électricité transfontalier** | - Montants des imports et exports d'électricité [TWh] et évolution par rapport à l'année précedente. | - Exports : 84 TWh (-2.7%)<br>- Imports : 28.3 TWh (+8.4%)   |
| **4. Structure du réseau**                   | - Lignes en exploitation [km]                                | - 105 942 km                                                 |
| **5. Emission du CO2**                       | - Emissions de CO2 du mix  [Mt] et évolution par rapport à l'année précedente. | -19Mt (-6%)                                                  |

> **Question 3**: : Pour les moyens dispatchables, reconstruire un module simple qui calcule le dispatch
> heure par heure. Pour cela, on utilisera en entrée les capacités installées de chaque filière et la courbe
> de demande nette. La demande nette est définie comme la consommation réelle à laquelle on
> soustrait la production des filières fatales et les imports/exports.

<img src="/home/elouan/Documents/ENPC/TEECO/figure4.1.png" alt="4.1 The Dispatch of Power Plants by an Electric Utility | EBF 483:  Introduction to Electricity Markets" style="zoom:33%;" />

<br><br> <br>

<br><br>

Grâce à un module python (cf annexe), nous pouvons déterminer le dispatch avec la courbe de demande et les moyens de production : 

<p float="center"><center>
    <img src="/home/elouan/Documents/ENPC/TEECO/dispatch_1.png" width="300">
    <img src="/home/elouan/Documents/ENPC/TEECO/dispatch_2.png" width="300">
    </center>
</p>



Voici donc deux dispatch possible avec en fonction du nombre de capacité plus au moins d'export ou import d'electricité. 

<img src="/home/elouan/Documents/ENPC/TEECO/conso_prod_reelle.png" alt="image-20210123233430586" style="zoom:40%;" />

Voici la vraie répartion du mix éléctrique :

##### Quelques remarques : 

* 

































## Partie 2 : Economie du stockage

>  Un actif de stockage se caractérise notamment par :
>
> * Une puissance installée en MW : Pmax
> * Une capacité de stock en MWh (quantité d’énergie maximale que l’on peut stocker) : Emax
> * Un rendement en % qui traduit les pertes qui interviennent lors du stockage/déstockage de
>   l’énergie

**2.1 Stockage journalier simplifié**

On considère une capacité de stockage de 1MW de puissance, et de stock 1MWh. On suppose que chaque jour la capacité de stockage réalise une charge puis une décharge (dans cet ordre). Pour simplifier, on considérera ici l’évaluation sur un seul mois : le mois de janvier 2020 (prix France). Etablir le fonctionnement de ce stockage, et estimer le bénéfice réalisé. Proposer une évaluation économique (simplifiée) de la rentabilité du stockage.



###### Fonctionnement du système de stockage : 

Le système de stockage a pour objectif de faire du profit en se chargeant quand le prix est faible (généralement la nuit) et en se déchargeant lorsque le prix est le plus elevé. Connaissant les caractéristiques du système de stokage : 

> **Caractéristiques du système de stockage**
>
> * $$ Energie = E_{max}$$ [MWh] :arrow_right: $$\boxed{E_{max} = 1MWh}$$ 
>   * Cela correspond au stock d'énergie dont dispose l'unité de stockage, et donc l'energie que peut absorber l'unité lors de la charge. 
> * $$ Puissance = P_{max}$$ [MWh] :arrow_right: $$\boxed{P_{max} = 1MW}$$ .
>   * En fonction de la puissance on connaît le temps qu'il faut pour charger l'unité, et la décharger. $$\boxed{E = P.\delta t}$$. **On charge donc l'unité de stockage en heure.** 
>
> * $$Rendement = \rho$$ . En fonction du rendement l'unité de stockage décharge sur le réseau $\boxed{E_{decharge} = \rho*E_{max}}$ (cf. Annexe rendement batterie)

**Economie du système:**

Avec une charge par jour et une décharge par jour, il faut donc que le système se charge lorsque le prix est le plus bas, et se décharge lorsque le prix est le plus elevé. 

> **Rentabilité du système** : Pour que le système puisse réaliser des profits sur la journée considérée, le rendement $\rho$ joue un **rôle crucial**.
>
> L'argent percue à la revente étant : $E_{decharge}.Prix_{revente} = \rho.E_{max}.Prix_{revente}$ il faut que :
>
> :arrow_right:$\rho.E_{max}.Prix_{revente} > E_{max}.Prix_{achat}$ soit $\boxed{\rho > \frac{Prix_{achat}}{Prix_{revente}}}$ 

*Pour expliquer ce point de vue voici deux graphiques, et le profit réalisé en fonction du rendement*:



<p float="center"><center>
    <img src="/home/elouan/Documents/ENPC/TEECO/rho_ok.png" width="300">
    <img src="/home/elouan/Documents/ENPC/TEECO/rho_nok.png" width="300">
    </center>
</p>

*Le 21/01 en fonction du rendement, il n'est pas forcément rentable d'opérer à une charge et à une décharge d'electricité :*

* Avec un $\rho=0.5$, le système de stockage n'est pas rentable, car il ne peut pas se charger et se décharger en réalisant un profit. Il faut donc envisager un rendement plus important avoir d'avoir une rentabilité.



##### Bilan pour plusieurs rendement sur un mois

*Nous pouvons désormais simuler les profits opéré sur un mois avec plusieurs valeurs de rendement, nous obtenons le tableau suivant :*

![image-20210116162222584](/home/elouan/.config/Typora/typora-user-images/image-20210116162222584.png)





Voici quelques éléments de réponse à tes questions :

Partie 1 Q3 : oui c'est tout à fait cette démarche qui est        attendu. Le graphe me semble bien. Ensuite l'objectif est de        comparer ce que tu as pu obtenir avec les données réelles afin        d'identifier les grandes différences et d'expliquer en quelques        mots pourquoi il y a des différences.

Partie 2

La formulation de la question 2 comporte effectivement une        erreur de signe comme tu le mentionnes. Pour le bilan        économique, il faut bien compter la charge en négatif (on paie        pour charger) et la décharge en positif (on gagne de l'argent        lorsqu'on décharge). Je vais corriger l'énoncé. Merci.





































# Annexe :

> Code disponible sur mon github : 



* $$ max \sum_{h \in heures} Prix(h)*(Edecharge(h) + Echarge(h))$$
* $$ 0 \leq Edecharge(h) \leq Pmax.\rho$$
* $$ -Pmax\leq Echarge(h) \leq 0$$
* $$ SoC(h+1)  = SoC(h) - Edecharge(h) +Echarge(h)$$
* $$ 0 \leq SoC(h) \leq Emax $$
* $$SoC(0) = 0$$



<img src="/home/elouan/Documents/ENPC/TEECO/effiency_battery.jpg" alt="Know your solar power system" style="zoom:33%;" />

