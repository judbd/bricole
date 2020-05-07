# Le problème

Égaux à eux-même, Adobe laisse trainer depuis des années des bugs sur la disposition des claviers (cf [mon gist pour un problème similaire avec illustrator non réglé depuis des années](https://gist.github.com/judbd/7249731), ce qui est un cauchemar quand votre clavier n'est pas en disposition américaine (qwerty). Sur lightroom, les raccourcis ne peuvent même pas être changés, ce qui interdit complètement l'accès à certaines fonctions. Et la doc traduite se contente de recopier les raccourcis US.

Après avoir failli devenir fou en essayant simplement d'accéder au réglage précédent et suivant (touches `,` et `.` en qwerty) j'ai fini par trouver où se cachaient ces options.

# La solution

## Localiser le fichier de traduction

Il faut localiser votre fichier de traduction `TranslatedStrings_Lr_fr_FR.txt`, qui se situe dans le répertoire d'installation de lightroom puis `Resources\fr` (ou votre code de langue si vous utilisez lightroom dans une autre langue. Pour l'anglais (qui est absent), vous pouvez créer un dossier `en` et utiliser le fichier d'une autre langue avec juste les paramètres nécessaires)

## Rechercher la fonction

Vous pouvez ensuite faire une recherche avec `key=x` où `x` est la touche du raccourci américain qui pose problème (mais des fois il est laissé vide). Vous pouvez aussi essayer de trouver la fonction par son nom en vous aidant du [tableau officiel](https://helpx.adobe.com/lightroom/help/keyboard-shortcuts.html)

## Modifier la fonction

Ensuite, il faut modifier le raccourci par une touche accessible directement sur votre clavier, dans mon cas, j'ai recherché ces lignes :

```
"$$$/AgDevelop/KBSC/targetNextAdjustment='"
"$$$/AgDevelop/KBSC/targetPreviousAdjustment="
```

_(notez l'absence de raccourci sur la 2e fonction)_

Que j'ai remplacées par :

```
"$$$/AgDevelop/KBSC/targetNextAdjustment='"
"$$$/AgDevelop/KBSC/targetPreviousAdjustment=-"
```

_ajout de la touche `-` comme raccourci de 2e fonction_

Prenez garde d'utiliser une touche qui n'est pas utilisée ailleurs pour ne pas crééer de conflits.

Relancez lightroom s'il était déjà lancé, ça devrait fonctionner.
