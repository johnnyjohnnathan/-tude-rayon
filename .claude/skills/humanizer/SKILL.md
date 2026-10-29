---
name: humanizer
description: Réécrit un texte pour retirer les tics d'écriture typiques des IA (formules creuses, triades, tirets cadratins, ton promotionnel, conclusions-résumés) et lui rendre une voix humaine, en français ou en anglais. À utiliser quand l'utilisateur tape /humanizer, demande d'« humaniser », de « rendre moins IA » ou de « faire naturel » un texte.
argument-hint: "[texte | chemin de fichier] [--ton familier|neutre|pro]"
---

# /humanizer

Réécris le texte fourni pour qu'il ne sonne plus comme une IA, sans changer le fond.

## Entrée

- `$ARGUMENTS` contient soit le texte, soit un chemin de fichier. Si c'est un chemin existant, lis le fichier.
- Rien de fourni : demande le texte. Ne devine pas.
- `--ton` optionnel (`familier`, `neutre`, `pro`). Par défaut : garde le registre de l'original.
- Garde la langue d'origine (français ou anglais).

## Règles de fond

- Ne rajoute aucun fait, chiffre, source ou exemple absent de l'original.
- Ne supprime aucune information réelle. Supprime seulement le remplissage.
- Si une phrase ne dit rien une fois le remplissage retiré, supprime-la.
- Garde les noms propres, chiffres, citations et termes techniques tels quels.

## Tics à éliminer

**Vocabulaire gonflé**
- FR : « crucial », « essentiel », « incontournable », « véritable », « au cœur de », « s'inscrire dans », « jouer un rôle clé », « témoigner de », « mettre en lumière », « un large éventail », « dans un monde en constante évolution », « n'hésitez pas à ».
- EN : delve, crucial, pivotal, vibrant, tapestry, testament, landscape, realm, seamless, robust, leverage, underscore, showcase, foster, navigate, "in today's fast-paced world".
- Remplace par le mot simple ou supprime.

**Structures mécaniques**
- Triades systématiques (« rapide, efficace et fiable ») : garde le nombre d'éléments que le sens exige.
- « Ce n'est pas X, c'est Y » / "It's not X, it's Y" : dis Y directement.
- Phrases en -ant qui ajoutent une pseudo-analyse (« …, soulignant ainsi l'importance de… ») : coupe.
- Questions rhétoriques suivies de leur réponse (« Le résultat ? Spectaculaire. »).
- Paragraphes tous de même longueur, phrases toutes de même rythme : varie.

**Ton**
- Enthousiasme promotionnel, superlatifs, « révolutionnaire », « passionnant ».
- Prudence excessive en cascade (« il pourrait éventuellement sembler que… ») : une seule nuance, là où elle est justifiée.
- Formules de service : « Excellente question », « J'espère que cela vous aide », « Bien sûr ! », "Certainly!".
- Conclusions-résumés : « En somme », « En conclusion », « Au final », "Overall", "In summary". Termine sur la dernière idée utile.

**Mise en forme**
- Tirets cadratins (—) en série : remplace par virgule, point, deux-points ou parenthèses.
- Gras décoratif, titres et listes à puces sur un texte qui devrait être de la prose.
- Listes « **Titre :** explication » : transforme en phrases si le contexte est un mail, un post ou un message.
- Émojis décoratifs.
- Typographie française : espaces insécables avant `: ; ? !`, guillemets « », pas de majuscule à chaque mot dans les titres.

## Ce qui rend un texte humain

- Phrases de longueurs inégales ; une phrase courte de temps en temps.
- Verbes concrets plutôt que noms abstraits (« on a décidé » plutôt que « la prise de décision a été effectuée »).
- Un point de vue assumé quand l'original en a un.
- Des transitions implicites plutôt que « De plus », « Par ailleurs », « En outre » en tête de chaque paragraphe.

## Sortie

1. Le texte réécrit, seul, prêt à copier. Pas de préambule.
2. Puis, sous un séparateur, 3 à 6 puces max : les principaux tics retirés. Omets cette partie si l'utilisateur demande « texte seul ».

Si l'entrée était un fichier, propose d'écrire la version réécrite dans le fichier ; ne l'écrase pas sans accord.
