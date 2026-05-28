# TP14 - Bypass de la détection root avec Frida, Objection et Medusa

Réalisé par **EZBIRI Amira**

## Contenu
Ce dossier contient :
- `snake_sslpinning_report.pdf` : rapport final au format PDF
- `snake_sslpinning_report.tex` : source LaTeX
- `README.md` : résumé de fonctionnement
- `figures/` : captures utilisées dans le rapport

## Objectif
L'objectif du TP est de neutraliser la détection root d'une application Android de test (`OWASP Uncrackable1`) à l'aide de :
- ADB
- Frida
- Objection
- Medusa

## Fichiers utiles
Les captures montrent notamment :
- le lancement de `frida-server` sur l'appareil ;
- la détection de l'appareil avec `adb devices` ;
- le message `Root detected!` dans l'application ;
- l'exécution de `android root disable` dans Objection ;
- les hooks Frida installés sur les fonctions de vérification ;
- l'analyse du périphérique avec Medusa.

## Étapes résumées
1. Préparer l'environnement : Python, ADB, Frida.
2. Démarrer `frida-server` sur l'appareil.
3. Vérifier la connexion avec `adb devices` et `frida-ps -Uai`.
4. Lancer l'application cible.
5. Appliquer le bypass root avec Frida ou Objection.
6. Observer le comportement de l'application après neutralisation.
7. Utiliser Medusa comme alternative ou complément.

## Commandes de base
```bash
adb devices
adb shell getprop ro.product.cpu.abi
adb push frida-server /data/local/tmp/
adb shell chmod 755 /data/local/tmp/frida-server
adb shell "/data/local/tmp/frida-server -l 0.0.0.0"
frida-ps -Uai
objection -g owasp.mstg.uncrackable1 explore --startup-command "android root disable"
```

## Remarques
- Le TP doit être exécuté uniquement sur un appareil autorisé.
- Si Frida ne se connecte pas, vérifie la correspondance des versions client/serveur.
- Si l'application crashe au spawn, essaye le mode `attach`.
- Si Objection ne suffit pas, complète avec un script Frida plus ciblé.

## Auteur
**EZBIRI Amira**
