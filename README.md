# Decoupage_reseau
Exercice Découpage réseau

# Symetrique:

Le réseau est 172.16.1.0/24
Nombre d'équipements par pôle 50 :

Adresses pôle informatique : 
Adresse de début : 172.16.1.0/26
Adresse de fin et broadcast : 172.16.1.63/26 

Adresses pôle développement :
Adresse de début : 172.16.1.64/26
Adresse de fin et broadcast : 172.16.1.127/26

Adresses pôle administratif :
Adresse de début : 172.16.1.128/26
Adresse de fin et broadcast : 172.16.1.191/26

Adresse pôle technicien : 
Adresse de début : 172.16.1.192/26
Adresse de fin et broadcast : 172.16.1.255/26

Methode de calcul pour découper les réseau de façon sysmétrique est la suivante :
calcul du masque réseau en prenant en compte le fait qu'il y a à minima 50 équipements par pôle, donc 62 IP (utilisables) ce qui représente 2 puissance de 6.
L'on fait alors le calcul de 32-6=26.
Puis on démarre à de l'adresse 172.16.1.0/26 et l'on ajoute 63 pour avoir l'adresse de fin et donc l'adresse de broadcast qui nous donne 172.16.1.63/26.
La première adresse du second pole sera la dernière adresse +1 qui nous donne 172.16.1.64/26 pour avoir le broadcast l'on fait +63 et ainsi de suite.

# Asymetrique:

Le Pôle Informatique : 50 équipements
Le Pôle Développement : 12 équipements
Le Pôle Administratif : 20 équipements
Le Pôle Technicien : 15 équipements

Le réseau est 172.16.1.0/24 

Adresses pôle informatique : 
Adresse de début : 172.16.1.0/26
Adresse de fin et broadcast : 172.16.1.63/26 

Adresse pôle développement :
Adresse de début : 172.16.1.0/28
Adresse de fin et broadcast : 172.16.1.15/28

Adresse pôle administratif :
Adresse de début : 172.16.1.32/27
Adresse de fin et broadcast : 172.16.1.63/27 

Adresse pôle technicien :
Adresse de début : 172.16.1.0/27
Adresse de fin et broadcast : 172.16.1.31/27 

Methode de calcul pour découper les réseau de façon asysmétrique est la suivante :
Calculer le masque réseau en prenant en compte le nombre d'équipements par pôle, exemple : pour 50 équipements on prendra des plages réseau de 64 IP donc des masques réseaux /26, pour des plages de réseau de 32 IP les masques seront /27. 
le calcul est le suivant : 32-la puissance de 2 du sous réseau concerné, ex: 32-6=26 32-5=27 32-4=28.
Puis on démarre à de l'adresse 172.16.1.0 et l'on ajoute le nombre de bit réseau en fonction de la plage réseau choisi 64, 32, ou 16 -1 pour avoir l'adresse de fin et donc l'adresse de broadcast.
Pour les plages réseaux des pôles administratif et technicien qui sont dans le même masque 27, on commence par le plus grand (le pole technicien) et l'on fait suivre le pôle administratif comme pour la méthode symétrique.

