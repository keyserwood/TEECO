<style type = "text/css">@page {size:letter;margin:-1em -3.5em -1em;text-align: justify;}//theme = academic & px = 12</style>		
<style> float-my-children {
    float:left;
    margin-right:5px;
}
</style>
<link rel="stylesheet" href="style.css">

<br><br>

<br>

<br>

<br>

<br>

<br>

<br>

<img src="https://www.ecoledesponts.fr/sites/ecoledesponts.fr/files/ckfinder/ckfinder/archives/l-ecole/3-ecole_ponts20_cmjn_600.jpg" alt="Charte graphique | ecoledesponts.fr" style="zoom:20%;" />

<div style='text-align:center;font-size:large;'>
    <br>École des Ponts ParisTech<br><br>
    01/02/2020
</div>

<div style='text-align:center;font-size:large;'>
    <p style='text-align:center;font-size:xx-large;'>
       Projet TEECO - Economie de l'énergie 
    </p>
</div><br>
<div style='text-align:center;font-size:x-large;'>
    <mark style="background-color: yellow;">Analyse de données du marché de l'électricité et optimisation</mark>
</div><br><br> 

<br>

<br>



<br>

<br>

<br>

<br>

<br>

<br>



<br>

<br>

<br>

<br>

<div style='text-align:center;font-size:medium;'>
    Elouan RAYMOND - ENPC 
</div>

<div style="page-break-after: always;"></div><br><br><br><br>

## Partie 1 : Le mix électrique français en 2019

#### Question 1 : L'origine des données 

> *Toutes les données nécessaires sont disponibles gratuitement en ligne. Voici quelques sites utiles :*
>	https://opendata.reseaux-energies.fr/pages/accueil/
> 	https://bilan-electrique-2019.rte-france.com/
> 	https://transparency.entsoe.eu/
> 
> *Qui fournit les donnés disponibles sur ces sites ? Pourquoi ?* 

<p style="text-align:justify;"><b>La loi  pour une république numérique</b> du 7 octobre 2016 (ou loi Lemaire) prévoit entres autres l'accès aux données publiques. L'Etat, les collectivités, les personnes de droit public ou de droit privés chargés d'une mission de service public doivent fournir des données. De nombreuses bases de données sont ainsi accessibles, comme le registre Sirene des entreprises, mais aussi les données liées à l'energie. <br>De nombreux acteurs de l'énergie public ou privée ont mis à disposition des données (hors données personnelles). <b>EDF</b> a mis en ligne les données propres à ses infrastructures, sa production et la consommation en Corse et en outre-mer. <b>Enedis et RTE</b> qui gèrent le réseau de distribution mettent en ligne les quantités d'électricité consommées et produites sur toute la France. GRTgaz et Teréga ont créé la plateforme opendata réseaux qui regroupent des acteurs privés afin de coupler données energétiques et données climatiques. Un accès et une mutualisation de ces données permet une <b>meilleure compréhénsion du système</b> et de <b>meilleures prises de décisions</b>, notamment grâce à des <b>analyses intersectorielles</b>.</p>

#### Question 2 : Le mix électrique

> Pour l’année 2019 uniquement, présenter les indicateurs clés permettant de comprendre le mix électrique français (côté demande et côté offre).

RTE réalise un bilan à la fin de chaque année pour faire un tour d'horizon de la production et de la consommation d'électricité dans le pays. 

*La synthèse s'articule autour de 5 grands axes  :* 

| Axe d'analyse                                | Indicateurs clés                                             | Valeurs pour 2019                                            |
| -------------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 1. **Production d'électricité**              | - Production totale d'électricité [TWh] et et évolution par rapport à l'année précédente [%]<br>- Part de chaque sources de production (nuclaire, hydraulique, éolien ...) [TWh] | -537.7 TWh produit (-2%)<br><br>Nucléaire(70.2%)\|Renouvelables(21.4%) |
| **2. Consommation**                          | - Consommation totale d'électricité [TWh] et évolution par rapport à l'année précédente [%] | - 473TWh consommé (-0.5%)                                    |
| **3. Echanges d'électricité transfontalier** | - Montants des imports et exports d'électricité [TWh] et évolution par rapport à l'année précedente. | - Exports : 84 TWh (-2.7%)<br>- Imports : 28.3 TWh (+8.4%)   |
| **4. Structure du réseau**                   | - Lignes en exploitation [km]                                | - 105 942 km                                                 |
| **5. Emission du CO2**                       | - Emissions de CO2 du mix  [Mt] et évolution par rapport à l'année précedente. | -19Mt (-6%)                                                  |

#### Question 3 : Le dispatch des moyens de production

> Pour les moyens dispatchables, reconstruire un module simple qui calcule le dispatch heure par heure. Pour cela, on utilisera en entrée les capacités installées de chaque filière et la courbe de demande nette.

<div style=" float:left;margin-right:5px;">
<img src="/home/elouan/Documents/ENPC/TEECO/report/img/figure4.1.png" alt="4.1 The Dispatch of Power Plants by an Electric Utility | EBF 483:  Introduction to Electricity Markets" style="zoom:33%;" />
</div>


<p style="text-align:justify;">Voici la représentation du dispatch que nous souhaitons reproduire. Pour ce faire, nous allons construire un module python qui prend en entrée la demande journalière et les capacités de productions disponibles. Si la <b>production</b> est <b>supérieure</b> à la <b>demande</b> <b>l'electricité</b> sera <b>exportée</b>. A l'inverse, Si la <b>production</b> est <b>inférieure</b> à la <b>demande</b> <b>l'electricité</b> sera <b>importée</b>. La capacité de production totale dépendra des capacités installées sur le système. Nous pourrons donc faire varier le dispatch en fonction du nombre d'outils de production. Le code est disponible en annexe.</p>

<div style="page-break-after: always;"></div><br><br>

Nous pouvons déterminer le dispatch avec la courbe de demande et les moyens de production : 

<p float="center"><center>
    <img src="/home/elouan/Documents/ENPC/TEECO/report/img/dispatch_1.png" width="300">
    <img src="/home/elouan/Documents/ENPC/TEECO/report/img/dispatch_2.png" width="300">
    </center>
</p>



Avec 4 outils de production d'une capacité suffisante, nous pouvons couvrir quasiment toute la demande, et même exporter une partie de l'electricité produite quand cela est nécessaire. A contrario avec 2 outils de production, il est nécessaire d'importer une grande quantité d'électricité afin de pallier au pic de consommation. 

Ci dessous, voici le vrai mix electrique de la journée du 01/01/2020, les données provenant de : https://opendata.reseaux-energies.fr/pages/accueil/.

<img src="/home/elouan/Documents/ENPC/TEECO/report/img/conso_prod_reelle.png" alt="image-20210124111221589" style="zoom:50%;" />

##### Quelques remarques : 

<p style="text-align:justify;">Par rapport au module python que nous avons implémenté, nous pouvons observer que la production totale est tout le temps bien supérieure à la consommation réelle.<br>Le nombre de moyens de production est bien entendu beaucoup plus varié : 10 moyens de production différents, avec toujours une part majoritaire d'électricité produite grâce au nucléaire. La production d'électricité via les énergies éoliennes et solaires reste assez marginale en ce premier jour de janvier. <br>La courbe de consommation est moins accentuée que celle que nous avons construire pour notre module, mais nous observons tout de même des variations logiques au cours de la journée.</p>

<div style="page-break-after: always;"></div><br><br><br>

## Partie 2 : Economie du stockage

>  Un actif de stockage se caractérise notamment par :
>
> * Une puissance installée en MW : Pmax
> * Une capacité de stock en MWh (quantité d’énergie maximale que l’on peut stocker) : Emax
> * Un rendement en % qui traduit les pertes qui interviennent lors du stockage/déstockage de
>   l’énergie

**2.1 Stockage journalier simplifié**

<p style="text-align:justify;">On considère une capacité de stockage de 1MW de puissance, et de stock 1MWh. On suppose que chaque jour la capacité de stockage réalise une charge puis une décharge (dans cet ordre). Pour simplifier, on considérera ici l’évaluation sur un seul mois : le mois de janvier 2020 (prix France). Etablir le fonctionnement de ce stockage, et estimer le bénéfice réalisé. Proposer une évaluation économique (simplifiée) de la rentabilité du stockage.</p>

#### Fonctionnement du système de stockage : 

Le système de stockage a pour objectif de faire du profit en se chargeant quand le prix est faible (généralement la nuit) et en se déchargeant lorsque le prix est le plus elevé. Connaissant les caractéristiques du système de stokage : 

> **Caractéristiques du système de stockage**
>
> * $$ Energie = E_{max}$$ [MWh] :arrow_right: $$\boxed{E_{max} = 1MWh}$$ 
>   * Cela correspond au stock d'énergie dont dispose l'unité de stockage, et donc l'energie que peut absorber l'unité lors de la charge. 
> * $$ Puissance = P_{max}$$ [MWh] :arrow_right: $$\boxed{P_{max} = 1MW}$$ .
>   * En fonction de la puissance on connaît le temps qu'il faut pour charger l'unité, et la décharger. $$\boxed{E = P.\delta t}$$. **On charge donc l'unité de stockage en une heure.** 
>* $$Rendement = \rho$$ . En fonction du rendement l'unité de stockage décharge sur le réseau $\boxed{E_{decharge} = \rho*E_{max}}$ (cf. Annexe [rendement batterie](#Fonctionnement d'une unité de stockage))

**Economie du système:**

Avec une charge par jour et une décharge par jour, il faut donc que le système se charge lorsque le prix est le plus bas, et se décharge lorsque le prix est le plus elevé. 

> **Rentabilité du système** : Pour que le système puisse réaliser des profits sur la journée considérée, le rendement $\rho$ joue un **rôle crucial**.
>
> L'argent percue à la revente étant : $E_{decharge}.Prix_{revente} = \rho.E_{max}.Prix_{revente}$ il faut que :
>
> :arrow_right:$\rho.E_{max}.Prix_{revente} > E_{max}.Prix_{achat}$ soit $\boxed{\rho > \frac{Prix_{achat}}{Prix_{revente}}}$ 

*Pour expliquer ce point de vue voici deux graphiques, et le profit réalisé en fonction du rendement*:

<p float="center"><center>
    <img src="/home/elouan/Documents/ENPC/TEECO/report/img/rho_ok.png" width="250">
    <img src="/home/elouan/Documents/ENPC/TEECO/report/img/rho_nok.png" width="250">
    </center>
</p>

<div style="page-break-after: always;"></div><br><br><br>


*Le 21/01 en fonction du rendement, il n'est pas forcément rentable d'opérer à une charge et à une décharge d'electricité :*

* Avec un $\rho=0.5$, le système de stockage **n'est pas rentable**, car il ne peut pas se charger et se décharger en réalisant un profit. Il faut donc envisager un rendement plus important avoir d'avoir une rentabilité.
* Avec un $\rho=0.7$, le système de stockage **est  rentable**, il peut  se charger et se décharger en réalisant un profit. 

#### Bilan pour plusieurs rendement sur un mois

*Nous pouvons désormais simuler les profits opéré sur un mois avec plusieurs valeurs de rendement, nous obtenons le tableau suivant :*

![image-20210116162222584](/home/elouan/.config/Typora/typora-user-images/image-20210116162222584.png)

Ainsi sur de nombreuses journées, un technologie de stockage avec un faible rendement ne permet pas de réaliser du profit. 

**Choix d'une technologie appropriée**

Le tableau en [annexe](#rendement-des-unités-de-stockages-en-fonction-de-la-technologie) permet d'avoir connaissance des différents types de technologies utilisables. On peut regrouper pour chaque type de technologies, par année, la moyenne du coût de ces installations (scénario de référence), le rendement (round-trip efficiency), et le ratio : $\frac{\rho}{Installation\:cost}$. 

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th></th>
      <th>Installation-cost-reference</th>
      <th>Rho</th>
      <th>Rho/Cost</th>
    </tr>
    <tr>
      <th>Year</th>
      <th>Type</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="5" valign="top">2016</th>
      <th>Lead-acid</th>
      <td>205.00</td>
      <td>81.00</td>
      <td>0.395122</td>
    </tr>
    <tr>
      <th>High- temperature</th>
      <td>383.50</td>
      <td>82.00</td>
      <td>0.213820</td>
    </tr>
    <tr>
      <th>Li-ion</th>
      <td>600.00</td>
      <td>94.50</td>
      <td>0.157500</td>
    </tr>
    <tr>
      <th>Flow</th>
      <td>623.50</td>
      <td>70.00</td>
      <td>0.112269</td>
    </tr>
    <tr>
      <th>Mechanical</th>
      <td>1024.67</td>
      <td>74.67</td>
      <td>0.072872</td>
    </tr>
    <tr>
      <th rowspan="5" valign="top">2030</th>
      <th>Lead-acid</th>
      <td>103.00</td>
      <td>84.00</td>
      <td>0.815534</td>
    </tr>
    <tr>
      <th>High- temperature</th>
      <td>161.50</td>
      <td>86.00</td>
      <td>0.532508</td>
    </tr>
    <tr>
      <th>Li-ion</th>
      <td>253.50</td>
      <td>96.50</td>
      <td>0.380671</td>
    </tr>
    <tr>
      <th>Flow</th>
      <td>214.00</td>
      <td>78.00</td>
      <td>0.364486</td>
    </tr>
    <tr>
      <th>Mechanical</th>
      <td>674.67</td>
      <td>78.33</td>
      <td>0.116101</td>
    </tr>
  </tbody>
</table>

Plus le ratio est elevé, et plus l'installation est intéressante. Voici les profits possibles sur la base des prix de 2016, avec *Lead-Acid* (0.81) ,*High-temperature* (0.82),*Li-ion* (0.94)  : 

<p float="center"><center>
    <img src="/home/elouan/Documents/ENPC/TEECO/report/img/choix_techno.png" width="250">
    <img src="/home/elouan/Documents/ENPC/TEECO/report/img/choix_techno2.png" width="500">
    </center>
</p>

Avec ces technologies on peut dégager un profit relativement intéressant, et en privilégiant le ratio $\frac{\rho}{Installation\:cost}$ le plus éléve - ici Lead-Acid. On minimise les frais d'installations, et on augmente donc la rentabilité du système, les CAPEX ayant une grande importance sur la rentabilité d'un projet.

<div style="page-break-after: always;"></div><br><br><br>

## Complexification de la modélisation du stockage (problème d’optimisation)

##### Formulation du problème d'optimisation 

$$ max \sum_{h \in heures} Prix(h)\times(-Edecharge(h)-Echarge(h))$$

**Sous contraintes :** 

​				$$0 \leq Echarge(h) \leq Pmax $$                                                          [1]

​				$$ -Pmax \leq Edecharge(h) \leq 0 $$                                                   [2]

​				$$ SoC(h+1) = SoC(h) + \rho.Echarge(h)+Edecharge $$          [3]

​				$$0 \leq SoC(h) \leq Emax $$                                                                  [4]

​				$$ SoC(0) = 0$$                                                                                   [5]

#### Résolution sous python avec OR Tools.

> Le code utilisé pour résoudre ce problème se trouve en annexe 

Une fois le problème d'optimisation implementé sous python, avec comme entrées : Prix mensuel, $\rho$, $P_{max}$, $ E_{max}$, on peut calculer les cycles de charge et décharge, l'evolution de la SoC (State of Charge) de la batterie et enfin le profit réalisé par le système.

<img src="/home/elouan/Documents/ENPC/TEECO/report/img/optim_pt2.png" alt="image-20210130123651520" style="zoom:52%;" />

La présence d'un rendement à l'entrée du système empêche la charge complète au premier cycle, ce qui explique les deux premières charges au début.

#### Visualisation du profit journalier 

<img src="/home/elouan/Documents/ENPC/TEECO/report/img/profit_optim.png" alt="image-20210130123729964" style="zoom:45%;" />

Si on compare avec les simulations réalisées précedemment, on observe que le profit mensuel pour $\rho = 0.81$ est désormais de 610.63€ contre 428€ auparavant.

 <div style="page-break-after: always;"></div><br><br><br>

#### Synthèse des profits avec 3 technologies différentes 

Sur la base des travaux effectués précedemment, on peut regarder l'évolution des profits pour les trois solutions : *Lead-Acid* (0.81) ,*High-temperature* (0.82),*Li-ion* (0.94).

<img src="/home/elouan/Documents/ENPC/TEECO/report/img/daily_profit.png" alt="image-20210130130423651" style="zoom:50%;" />

<img src="/home/elouan/Documents/ENPC/TEECO/report/img/cumsum_comp.png" alt="image-20210130131245402" style="zoom:50%;" />



Pour comparer l'évolution par rapport aux résultats précédénts : 

| Solution                         | Profits sans optim | Profits avec optim | % augmentation |
| -------------------------------- | ------------------ | ------------------ | -------------- |
| Lead acid : $\rho$ = 0.81        | 428€               | 610.63€            | + 42.6%        |
| High temperature : $\rho$ = 0.82 | 443€               | 632.22€            | + 42.7%        |
| Li-ion : $\rho$ = 0.94           | 635€               | 912.96€            | + 43.7%        |





> **Conclusion** : L'optimisation du système de revenus heure par heure avec des contraintes permet donc d'améliorer de façon significative (+42%) le profit réalisé sur le mois de janvier.  Une fois de plus en optimisant le ratio $\frac{\rho}{Installation\:cost}$, on dispose d'une installation de stockage performante avec des coûts d'installation les plus faibles possibles. 

<div style="page-break-after: always;"></div><br><br><br>

## Annexe :

> Code disponible sur mon github : https://github.com/keyserwood/TEECO



##### Fonctionnement d'une unité de stockage

<img src="/home/elouan/Documents/ENPC/TEECO/report/img/effiency_battery.jpg" alt="Know your solar power system" style="zoom:33%;" />

##### Rendement des unités de stockages en fonction de la technologie

<img src="/home/elouan/Documents/ENPC/TEECO/report/img/caracteristiques_tech_stockage.png" alt="image-20210124114632489" style="zoom:67%;" />