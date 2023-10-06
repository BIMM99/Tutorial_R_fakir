# Didacticiel 03 : Générer des données factices à des fins pédagogiques avec fakir.

Tutoriel réalisé par Benoît MARION. 

Masters APE-SEP et MA-SEP, 2ème année, année universitaire 2023-2024.

<br><center> <img src="https://thinkr-open.github.io/fakir/reference/figures/logo.png" alt="Fakir logo" width="200"/>
<figcaption>Logo Fakir</center><br>

## Contexte

Dans le cadre d'un apprentissage de la manipulation et de la visualisation de données, il est souvent utile de travailler sur des bases qui ressemblent à des cas pratiques afin de s'entraîner au plus proche de ce qui existe dans des situations réelles. Cependant, les données accessibles librement sont souvent très agrégées (région...) ou ayant peu de sens dans un cadre proche de besoins professionnels dans le monde de la donnée (la fameuse base `iris` par exemple).

C'est pour répondre à ces problématiques que [`fakir`](https://cran.r-project.org/web/packages/fakir/index.html) a été créé. Développé par deux développeurs français [Colin Fay](https://colinfay.me/) (*maintainer*) et [Sebastien Rochette](https://statnmap.com/), il permet d'obtenir des jeux de données factices se rapprochant de ceux qui se trouvent dans un environnement réel (données de sondage, avis client ...). Cela permet donc de travailler sur des données plus pertinentes pour des cas pratiques tout en respectant la RGPD.

L'objectif est aussi de permettre d'avoir facilement des *datasets* pour travailler la manipulation (`tidyverse` principalement) et la visualisation de données (`ggplot` ou `shiny`).

Ainsi, comme l'expliquent les auteurs sur le [wiki de fakir](https://thinkr-open.github.io/fakir/index.html): 

> "Certains jeux de données suivent les principes du *tidy-data*, d'autres non. Certaines valeurs sont manquantes pour les données numériques et catégorielles. Certaines variables sont corrélées"

## Pré-requis

* R, RStudio ou autre IDE (espace de développement intégré) prenant en compte R (Visual Studio Code par exemple).
* installer le package `fakir`, `ggplot2`, `dplyr` et `sf`(avec la commande `install.packages()` dans la console R ou l'interface RStudio).
* Quarto (inclus avec RStudio depuis la v2022.07.1, voir [ici](https://quarto.org/docs/download/) pour plus de détails) qui permet de créer des documents mêlant code et texte formaté (en markdown). Il y aura un fichier R simple dans le dépôt pour ceux qui préfèrent lancer le script ou aller ligne de code par ligne de code.

## Les fonctions de fakir, en bref
Les fonctions du package fakir renvoient 5 types de jeu de données différents :

- une fausse liste de produits (`fake_product()`)
- un faux registre des visites quotidiennes sur un site (`fake_visits()`)
- un fausse liste d'évaluation par les clients (`fake_user_feedback()`)
- les fausses réponses à sondage sur les habitudes de transport (`fake_survey_people()` pour avoir juste les répondants ou `fake_survey_answer()` les répondants et leur réponses)
- une fausse base de clients et leur tickets pour un service de support (`fake base_clients()` pour avoir juste une liste de clients ou `fake_ticket_client()` pour avoir les clients et leur ticket)

Pour schématiser, 4 différents arguments peuvent être envoyés aux fonctions :

- `seed` permet de déterminer l'initialisation du générateur pseudo-aléatoire afin d'avoir des résultats réplicable (si utilisation de la même graine), elle dispose d'une valeur par défaut de 2811.
- `n` pour sélectionner le nombre de ligne du jeu de données en sortie (pour `fake_visits()` c'est la date de début et la date de fin qui détermine `n`)
- `local` permet de choisir entre avoir les données avec des informations (nom, prénom) françaises ou étasuniennes pour des faux-client.
- `split` qui, pour les jeux de données qui sont issus de jointure (client et leurs ticket pour `fake_client_...()`, réponse et répondant pour `fake_survey_...()`), permet de choisir si l'on veut deux base (`split = TRUE`) ou une seule (`split = FALSE`)

C'est donc un package relativement simple qui permet d'avoir rapidement des données factices relativement semblables à des données réelles.

## Documents présents dans le dépôt
* ce `README.md` qui fait office d'introduction et de sommaire
* un document `fakir_guide.Qmd` qui est un guide (mêlant code et explications) qui j'ai essayé de faire le plus exhaustif possible, il reprend quelques extraits de ce document. Le code brut avec quelques indications est disponible dans le fichier `fakir_guide.R` pour ceux qui préfèrent "le ligne par ligne".
* un fichier `fakir_guide.html` qui est juste le rendu du fichier Quarto pour que vous puissiez le passer en revue plus facilement et sans exécuter le code.
* un fichier `fakir_manual.pdf` qui est le manuel de référence réalisé par les auteurs et disponible dans le site du CRAN, j'ai préféré l'ajouter au dépôt.

La vidéo associée à ce guide n'est pas dans le dépôt et sera disponible ultérieurement.

## Quelques ressources complémentaires 

<p>Fay C, Rochette S (2023).
CRAN repository : <em>fakir: Generate Fake Datasets for Prototyping and Teaching</em>.
R package version 1.0.0, <a href="https://cran.r-project.org/web/packages/fakir/index.html" class="external-link">https://cran.r-project.org/web/packages/fakir/index.html</a>. 
</p>

<p>Fay C, Rochette S (2023).
Code & git repository : <em>fakir: Create Fake Data in R for tutorials</em>.
R package version 1.0.0, <a href="https://github.com/Thinkr-open/fakir" class="external-link">https://github.com/Thinkr-open/fakir</a>. 
</p>

<p>Fay C, Rochette S (2023).
Docs <em>Package ‘fakir’ - user guide,</em>
<a href="https://cran.r-project.org/web/packages/fakir/fakir.pdf" class="external-link">https://cran.r-project.org/web/packages/fakir/fakir.pdf</a>. 
</p>

<p>AbdulMajedRaja RS (2019).
Blog : <em>Create fake but meaningful data using {fakir}, </em><a href="https://towardsdatascience.com/create-fake-but-meaningful-data-using-fakir-b193df1f4c94" class="external-link">https://towardsdatascience.com/create-fake-but-meaningful-data-using-fakir-b193df1f4c94</a>. 
</p>

<p> Dima Diachkov (2023).
Blog : <em>How to create purely fictional datasets in R with the fakir package, </em><a href="https://blog.devgenius.io/how-to-create-purely-fictional-datasets-in-r-with-fakir-package-5c527516c682" class="external-link">https://blog.devgenius.io/how-to-create-purely-fictional-datasets-in-r-with-fakir-package-5c527516c682
</a>
</p>

<p>1littlecode (2020).
Vidéo : <em>Create meaningful fake tidy datasets in R using fakir [#rstats Package], </em><a href="https://www.youtube.com/watch?v=EhhljL5zaWs" class="external-link">https://www.youtube.com/watch?v=EhhljL5zaWs</a>. 
</p>
