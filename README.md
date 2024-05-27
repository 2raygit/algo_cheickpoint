# algo_cheickpoint
# Analyse de Phrase

Ce projet contient un algorithme pour analyser une phrase. L'algorithme lit une phrase se terminant par un point, caractère par caractère, et détermine :

1. La longueur de la phrase (le nombre de caractères).
2. Le nombre de mots dans la phrase (en supposant que les mots soient séparés par un seul espace).
3. Le nombre de voyelles dans la phrase.

## Structure de l'Algorithme

L'algorithme est défini comme suit :

```plaintext
ALGORITHM analyse_phrase
VAR
    longueur_phrase : INTEGER       // Compteur pour la longueur de la phrase
    nombre_mots : INTEGER           // Compteur pour le nombre de mots
    nombre_voyelles : INTEGER       // Compteur pour le nombre de voyelles
    voyelles : STRING               // Chaîne contenant toutes les voyelles
    in_word : BOOLEAN               // Indicateur pour savoir si on est dans un mot
    char : CHAR                     // Caractère courant lu
BEGIN
    longueur_phrase := 0            // Initialiser la longueur de la phrase à 0
    nombre_mots := 0                // Initialiser le nombre de mots à 0
    nombre_voyelles := 0            // Initialiser le nombre de voyelles à 0
    voyelles := "aeiouyAEIOUY"      // Définir les voyelles
    in_word := FALSE                // Initialiser l'indicateur de mot à FALSE

    WHILE TRUE DO
        READ char                   // Lire un caractère
        IF char = '.' THEN          // Si le caractère est un point, sortir de la boucle
            EXIT
        END_IF

        longueur_phrase := longueur_phrase + 1  // Incrémenter la longueur de la phrase

        IF char IN voyelles THEN     // Si le caractère est une voyelle
            nombre_voyelles := nombre_voyelles + 1  // Incrémenter le compteur de voyelles
        END_IF

        IF char = ' ' THEN           // Si le caractère est un espace
            IF in_word THEN          // Si on était dans un mot
                nombre_mots := nombre_mots + 1  // Incrémenter le compteur de mots
                in_word := FALSE     // Indiquer qu'on est plus dans un mot
            END_IF
        ELSE
            in_word := TRUE          // Sinon, indiquer qu'on est dans un mot
        END_IF
    END_WHILE

    IF in_word THEN                  // Après la boucle, si on est encore dans un mot
        nombre_mots := nombre_mots + 1  // Incrémenter le compteur de mots
    END_IF

    PRINT "Longueur de la phrase : ", longueur_phrase  // Afficher la longueur de la phrase
    PRINT "Nombre de mots : ", nombre_mots            // Afficher le nombre de mots
    PRINT "Nombre de voyelles : ", nombre_voyelles    // Afficher le nombre de voyelles
END
