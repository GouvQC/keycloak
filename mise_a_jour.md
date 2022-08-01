# Mettre à jour GouvQC/keycloak 

## Objectif

Procédure pour mettre à jour https://github.com/GouvQC/keycloak à partir de l'original avec les tags

## Procédures

### Préalables
  - Un compte GitHub avec les droits en écriture sur GouvQC/keycloak
  - Un jeton d'accès GitHub (Personal Access Token) sur ce compte

### Préparatifs

1. Cloner https://github.com/GouvQC/keycloak sur une machine locale
2. S'authentifier au push en utilisant le *PAT*

    `git remote set-url origin https://PAT:PAT@github.com/GouvQC/keycloak/`
    
3. Créer la branche de sauvegarde *NOM_BRANCHE*
    
	  `git checkout -b NOM_BRANCHE main`
    
	  `git push --set-upstream origin NOM_BRANCHE`
    
4. Retourner à la main
    
	  `git checkout main`
    
5. Prendre en note l'identifiant (*HASH*) du plus récent commit produit par la commande suivante
    
    `git rev-parse HEAD`
    

### Mise à jour

1. Créer un lien upstream vers l'original

	  `git remote add upstream https://github.com/keycloak/keycloak.git`
    
2. Aller chercher l'original avec les tags.

    `git pull upstream main --rebase --tags`
  
    S'il refuse de mettre à jour des tags, vous pouvez utiliser force (ce n'est pas recommandé)
    
    `git pull upstream main --rebase --tags --force`
    
4. Transmettre les changements
	  
    `git push origin main --force --tags`
    

### Retour en arrière

En cas d'erreur, il est possible de remettre le dépôt vers son état original

1. Faire un reset vers le bon commit
	  
    `git reset --hard *HASH*`
    
2. Envoyer le reset	
	  
    `git push origin main --force`
    
