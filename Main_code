from gpiozero import Button #lecture du signal de la sonde sur la broche GPIO
from time import sleep, time #gestion du temps, sleep pour pause et time pour heure actuelle

PIN = 17 #numéro de la broche GPIO où est branchée la sortie de la sonde
FENETRE = 10  #durée de mesure des impulsions en secondes

#compte le nb d'impilsions reçues
compteur = 0


#fonction appelée à chaque impulsion, modifie valeur du compteur en dehors de la fonction
def impulsion():
    global compteur
    compteur += 1

#broche à 0 V au repos, impulsion la passe à 3,3 V, mets True si la sonde fait l’inverse
sonde = Button(PIN, pull_up=False, bounce_time=None)
sonde.when_pressed = impulsion #à chaque impulsion sur la broche execution de la fonction impulsion

#compte les impulsions envoyées par la sonde et affiche toutes les 10s:
#taux de comptage en coups par seconde (CPS)
#taux de comptage en coups par minute (CPM).
while True:
    compteur = 0
    debut = time()
    sleep(FENETRE)
    duree = time() - debut
    cps = compteur / duree
    print(f"{cps:.2f} coups/s  ({cps * 60:.0f} CPM)")


