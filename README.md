# Export_a_Soi
Repository pour export pandoc Md vers PDF avec template LateX

Ce qu'il contient : 

- texte.md : fichier pour le corps de texte incluant les métadonnées (YAML)
- bib.bib : fichier pour la bibliographie
- template1.tex : template LaTeX pour la mise en page de l'Udem
- template2.tex : template LaTeX pour la mise en page d'une proposition d'article
- 2 fichiers de style bibliographique : udem-apa.csl et chicago-author-date.csl

## Rédaction/Édition

Éditer le texte.md avec les informations suivantes : 

1. Métadonnées 

Adapter les métadonnées suivantes : 

```
--- 
author: 
    - forname: Prénom
    - surname: Nom
    - institution: Université de Montréal
teacher: 
  - forname: Prénom
    surname: Nom
title: Titre
subtitle: sous-titre
year: 2023
month: Mars
day: 21
cours:
  - id: FRA3825
    title: Pratiques de l'édition numérique
nocite: '@*'
---
```

2. Corps de texte 

Rédiger votre proposition de projet d'écriture. 

400-500 mots. 

3. Enrichissement

Si nécessaire, éditer votre texte (italique, mise en gras, tirets longs, hyperliens, références, niveaux de titre, appels de note, etc.).

**Rappel**

- Le dernier titre doit être celui de la bibliographie
- Pas de titre de niveau 1 dans le corps du texte


## Conversion/Production

Dans votre terminal, 

1. Md vers Tex

Lancer la commande selon vos choix de template et de style bibliographique : 

```
pandoc --standalone --bibliography=bib.bib --template=template1.latex --csl=udem-apa.csl -f markdown -t latex texte.md -o texte.tex
```

Si vous souhaitez convertir avec le template 2, il faut remplacer `template1.md` par `template2.md` dans la commande. 

Si vous souhaitez le style bibliographique de Chicago, il faut remplacer `udem-apa.csl` par `chicago-author-date.csl`.

*Durant la conversion, beaucoup de fichiers vont être créés, il faut les conserver mais ils ne nous intéressent pas en tant que tels.*

2. Tex vers PDF

Lancer la commande suivante : 

```
xelatex texte.tex 
```

**Rappel** 
- Si vous changez les noms des fichiers, il faut les changer dans les commandes. 

## Gestion/Diffusion 

Vous allez maintenant pusher votre PDF sur le repository *Export à soi* sur votre propre branche. 

Pour ce faire : 

Premier réflexe : 

```
git pull

```

Se placer sur sa branche (le nom de la branche est ici *margot*) : 

```
git switch margot
```

Ajouter ses modifications : 

```
git add sichiers_modifiés.extension
```

Commiter ses modifications : 

```
git commit -m "mon commentaire qui décrit ce que j'ai fait"
```

Pusher ses modifitions : 

```
git push --set-upstream origin margot_by_switch
```

Pour vérifier que tout est à jour sur sa branche : 

```
git status
```

## Conseils 

Rappel : Votre terminal est votre ami, ce qui ne veut pas dire qu'il vous aime mais qu'il vous informe quand il y a une erreur dans les fichiers.tex si vous avez modifié le template. 

Astuce : pour corriger les erreurs, vous pouvez utiliser la plateforme [Overleaf](https://fr.overleaf.com/).



## Pour aller plus loin (Facultatif)

#### Je souhaite citer des références dans le texte 

Même édition que dans Stylo : il faut insérer la clef bibtex à l'endroit souhaité. 

#### Je souhaite un autre style bibliographique : 

- importer le fichier du style bibliographique en .csl dans le dossier et modifier la commande selon le nom du fichier de style bibliographique 

#### Je souhaite séparer ma bibliographie de mon corps de texte 

Deux possibilités : 

- soit je place la balise `\newpage` directement dans mon fichier.md avant le titre de la Bibliographie 

```

\newpage

## Bibliographie

```

- soit je place la balise `\newpage` dans le fichier.tex (une fois produit) **avant** de lancer la commande `xelatex texte.tex` comme suit.

```

\newpage

\hypertarget{bibliographie}{%
\subsection*{Bibliographie}\label{bibliographie}}
\addcontentsline{toc}{subsection}{Bibliographie}


```

*La deuxième option force à refaire l'opération après chaque conversion md vers tex.*

#### Je souhaite changer les couleurs utilisées 
 
Choisir la couleur à partir des labels listés [ici](https://www.latextemplates.com/svgnames-colors).

- pour les liens internes (appels de note) : modifier le nom dans à la ligne 152 (Template 1) ou ligne 86 (Template 2). 

```
linkcolor= Blue,
```

- pour les liens externes (hyperliens) : modifier la ligne 151(Template 1) ou ligne 85 (Template 2). 

```
urlcolor= TealBlue,
```

- pour les lignes (seulement dans le Template 2) : modifier la ligne 43 pour changer le trait en bas de page, 

```
\xpretocmd{\footrule}{\color{TealBlue}}{}{}
```

modifier la ligne 237 pour le trait de haut de page. 

```
\color{TealBlue}\hrule
```

#### Je souhaite ajouter une image 

Uploader l'image dans le bon dossier (*media*).

Éditer votre image en markdown : 

```
![légende](chemin)
```
