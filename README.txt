Application de votes entre une catapulte ou un tébuchet

 1 - Création d'un cluster de dev (kubernetes) comprenant 3 noeuds (voire un noeud comme une machine virtuel ou physique)

 2 - Création d'un fichier descriptor.yml (voir fichier), celui ci sert à décire le nombre de pods utilisé
    un pod contendra une image docker d'un service/protocol/OS/Application/..., autrement appeler conteneur

    - Un pod sera charger de la partie front end (le front est en static avec de l'ajax)
    - Un pod pour la partie back end (le back end est en nodeJs)
    - Un pod pour la database mysql

3 - Création d'un service mysql étant charger de rediriger toutes les arrivées sur le port 3306 vers le port 3306 du pod mysql (voir fichier mysql-svc.yml)

4 - Création d'un service api servant à rediriger toutes les arrivées du port 80 vers le port 80 du pod back end port 80 (voir fichier api-svc.yml)

5 - Création d'un service front servant à rediriger ce qui nous arrive de l'exterieur du port 80 vers le pod front end port 80 (voir fichier front-svc.yml)

6 - Utilisation de Ingress ce service rendra accessible notre application depuis l'extérieur
    Il faut installer un controlleur pour ce faire on à utilisé Traefik
        utilisation de ce tuto : https://blog.zenika.com/2018/04/27/traefik-comme-reverse-proxy-sur-gke/
        a partir de la partie : Création des autorisations pour Traefik
        (NE PAS METTRE D'IP FIXE comme indiquer dans le tuto, laissé kubernetes gérer l'IP extérieur)

