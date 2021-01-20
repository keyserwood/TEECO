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

<img src="/home/elouan/.config/Typora/typora-user-images/image-20210120155915703.png" alt="image-20210120155915703" style="zoom:50%;" />



*Construire un script python (1h-1h30)*

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
> * $$Rendement = \rho$$ . En fonction du rendement l'unité de stockage décharge sur le réseau $\boxed{E_{decharge} = \rho*E_{max}}$

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

















































# Annexe :

### Partie 1 : Module python pour le calcul du dispatch 

```python
hours = [i for i in range(24)]
demande = [50,45,40,40,40,40,40,40,40,45,50,55,60,60,60,70,70,70,65,60,57,53,50,50]
capacity = [30,20,10,5]
```

<br> 

```python
def dispatch(demande, capacity):
    capacity.sort(reverse=True)
    # Il faut d'abord créer le dispatch, pour cela on utilise une matrice afin de savoir quelle unité sont utilisée à quelle heure
    mat = np.zeros((len(capacity)+1,24))
    capacities = np.zeros((len(capacity)+1,24))
    for (i,d) in enumerate(demande) : 
        # Pour chaque demande horaire, nous devons calculer le dispatch adéquat
        r = d 
        j = 0
        while r!=0 and j<len(capacity) :
                if capacity[j] < r:
                    # Cette capacité n'est pas suffisante pour répondre à la demande
                    r = r-capacity[j]
                    mat[j][i] = 1
                else :
                    # La capacité  est supérieure à ce dont nous avons besoin on n'en utilisera qu'une partie 
                    r = 0
                    mat[j][i] = 1
                    # signifie que nous allons exporter l'énergie résiduelle 
                    mat[len(capacity)][i] = -1

                j+=1
        if r!=0:
            mat[len(capacity)][i] = 1
    #Ensuite on créé les vecteurs qui vont nous permettre d'afficher le dispatch
    for i in range(len(hours)):
        #### On parcourt chaque heure
        maxcap_h = 0 #Permet de savoir quelle est le niveau minimum de production pour chaque heure utile pour tracer
        for j in range(len(capacity)+1):
            if j!=len(capacity):
                if mat[j][i] !=0:
                    capacities[j][i] = sum(capacity[:j+1]) #On définit la capacité
                    maxcap_h = capacities[j][i]
                else :
                    capacities[j][i] = maxcap_h

            else : 
                if mat[j][i]!=0:
                    # Les unités de production ne sont pas suffisante, ou trop importantes, il faut importer // exporter
                    capacities[j][i] = (demande[i]-sum(capacity))
    plot_dispatch(demande,capacity,capacities,mat)
    return(mat,capacities)
```

