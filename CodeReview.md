Code review de marine corrigé par Adrien sur l'exercice 3

Bonne idée de faire un json des listes des chambre froide 1,2 et 3.
___________________________________ 
for row in contenu_csv:
        chambre = row[2] 
        try:
            temperature = float(row[3].replace(',', '.'))
            if chambre in chambres_data: 
                chambres_data[chambre].append(temperature)
        except ValueError:
            continue

ce for permet de trier facilement les températures
__________________________________

Pour l'affichage tu aurais pu faire 
' '*15 au lieu d'ecrire 15 fois espace (plus propre)

____________________________________________________

   minimum = float('inf')
   maximum = float('-inf') 

    ici vaut mieux initier le min a 99 et le max a 0 mais ta facon de faire marche aussi
____________________________________________________
    for temporaire in chambres_data[chambre]:
        if temporaire > maximum:
            maximum = temporaire
        if temporaire < minimum:
            minimum = temporaire
        total += temporaire
        nombre_temporaire += 1

        par contre le try except autant le mettre sur tout le programme (la methode bubble up)

ici ta fonction est pratique car elle trie a la fois le min, le max et fait la somme des températures de chaque chambre (pour la diviser par la taille par la suite)
mais par contre il existait deja des fonctions toute faite pour récuperer le min et le max sur python min(list) et max(list). pareil la variable nombre temporaire qui sert a avoir la lenght il existe la fonction len(list) et vaut mieux l'appeler autrement que nombre temporaire pour que ce soit plus parlant tel que taille_liste ou length.

if nombre_temporaire > 0:  ici la condition peut etre enlever car on bosse avec une base de fichier et donc forcement pas vide.
_______________________________________________________

print(f"{chambre:15} {round(total / nombre_temporaire, 1):5} {minimum:5} {maximum:5}")

les délimiteurs d'espace :15 :5 c'est tres bien comme ca c'est sûr qu'on est un bon format d'affichage.
