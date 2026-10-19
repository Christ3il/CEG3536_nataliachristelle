# JOURNAL — équipe NataliaChristelle
## Membres et rôles
- Natalia : réalise (séance 0), valide (séance 1)
- Christelle : valide (séance 0), réalise (séance 1)
## J1 — 25 septembre
- Exigences E1–E9 reformulées
- Échéancier labs 1–5 (dates du plan de cours)
- Répartition et rotation des rôles
## Séance 0 — 18 sept.
- Présents : Natalia, Christelle
- Fait : projet, LD3, débogueur
- Mesures : MODER = 0xABF7FFFF
- Problèmes : ...
## J1 — 11 octobre
  ### EXIGENCES
  - E1 : état ARRÊT, seule la DEL rouge allumée dans les 100 ms.
  - E2 : appuis validés sur User passant par ARRÊT → MARCHE_AVANT → ARRÊT → MARCHE_ARRIÈRE → ARRÊT.
  - E3 : Fenêtre d’anti-rebond de 20 à 50 ms.
  - E4 : appui sur E-Stop déclenche l’interruption EXTI2.
  - E5 : En ARRÊT_URGENCE, la DEL rouge clignote; les DEL verte et bleue sont éteintes.
  - E6 : appui validé sur Touch En, E-Stop est relâché.
  - E7 : Hors ARRÊT_URGENCE, chaque appui validé sur Touch En inverse une variable d’autorisation.
  - E8 : Les durées proviennent d’une routinedelay_ms documentée.
  - E9 : Appuis simultanés sur User et Touch En.
  ### ÉCHÉANCIER 
#### labo 2 séance 1 -  9 oct.
- Rôles : Christelle réalise, Natalia valide
#### labo 2 séance 2 - 16 oct.
- Rôles : Natalia réalise, Christelle valide
- Remise : 21 0ct.
#### labo 3 séance 1 -  23 oct.
- Rôles : Christelle réalise, Natalia valide
#### labo 3 séance 2 - 6 nov.
- Rôles : Natalia réalise, Christelle valide
- Remise : 13 nov.
- Jalon 2 : 6 nov. 
#### labo 4 séance 1 -  13 nov.
- Rôles : Christelle réalise, Natalia valide
#### labo 4 séance 2 - 20 nov.
- Rôles : Natalia réalise, Christelle valide
- Remise : 27 nov.
#### labo 5 séance 1 -  27 nov.
- Rôles : Christelle réalise, Natalia valide
#### labo 5 séance 2 - 4 dec.
- Rôles : Natalia réalise, Christelle valide
- Remise : 9 dec.
- Jalon 3 : 27 nov.
## labo 1 Séance 1 — 22 / 25 sept.
- Présents : Natalia, Christelle
- Rôles : Christelle réalise, Natalia valide
- Fait : fsm_step (E2), button_pressed (E3)
- Mesures : rebond 8 ms sur PC13 fenêtre retenue 30 ms
## labo 1 Séance 2 — 2 oct.
- Présents : Natalia, Christelle
- Rôles : Natalia réalise, Christelle valide
- Fait : estop_init et EXTI2_IRQHandler (E4), Clignotement à 2 Hz et acquittement (E5, E6), Touch En (E7),
- Mesures : période de clignotement et délai E-Stop aux points de test (T5, T6)

# JOURNAL.md — Journal d'équipe, CEG 3536, laboratoire 2 (automne 2026)

Équipe : `Christelle` et `Natalia` — Section : `A01` — Dépôt Git : `<adresse>`

## Suivi du jalon J1

| Laboratoire | Échéancier prévu (J1) | Déroulement réel | Écart et cause | Ajustement pour les laboratoires 3 à 5 |
|---|---|---|---|---|
| 1 | | | | |
| 2 | | | | |

## Rôles et rotation

| Séance | Réalise | Valide (essais, mesures, relecture) | Périphérique configuré ou mesuré par chacun |
|---|---|---|---|
| Séance 1 (16 oct.) |Christelle |Natalia |Christelle |
| Séance 2 (23 oct.) |Natalia |Christelle |Natalia |

## Calculs préalables (avant la séance 1)

| Grandeur | Formule | Valeur | Vérifiée par (essai) |
|---|---|---|---|
| `PWM_PSC`, `PWM_ARR` | f = 4 MHz / ((PSC + 1)(ARR + 1)) = 20 kHz |PSC=0, ARR=199 | T3 |
| `CCR1` pour 25 / 50 / 75 / 100 % | pct × (ARR + 1) / 100 |50/100!150/200 | T3 |
| `SYSTICK_LOAD_1MS` | 4 MHz × 1 ms − 1 |ARR = 99 : 100 pas, 1 %| T10 |
| Fronts par tour (arbre de sortie) | 2 × 11 × 34 | | T5 |
| tr/min à partir de `vitesse_fronts` | fronts × 120 / 748 (fenêtre 500 ms) |ARR = 399 : 400 pas, 0,25 %| T6 |
| Fronts attendus par fenêtre de 500 ms à 100 % | 350 tr/min (arbre de sortie) × 748 / 120 |400 kHz sur PE9 | T6 |

## Journal labo2

### Séance 1 — `16 oct.` — réalise : `Christelle` / valide : `Natalia`
- Objectifs :
- Fait :
- Décisions (sens réel de rotation pour AI1 = 1, AI2 = 0 ; `ENC_SENS_INVERSE` ; variante buzzer) :
- Difficultés et solutions :
- Mesures (PWM, SysTick, bips) :
- Validations Git (auteur, message) :

### Séance 2 — `23 oct` — réalise : `Natalia` / valide : `Christelle`
- Objectifs :
- Fait :
- Décisions :
- Difficultés et solutions :
- Mesures (encodeurs, vitesse, délai E-Stop) :
- Validations Git :

## Tableau des mesures (composante L2-A)

| Mesure | Exigence | Valeur mesurée | Incertitude / méthode | Écart | Cause | Preuve (fichier) |
|---|---|---|---|---|---|---|
| Fréquence PWM | 20 kHz ± 5 % | | | | | |
| Rapport cyclique à 25 / 50 / 75 / 100 % | ± 2 points | | | | | |
| Rampe 0 → 100 % | 1 s ± 10 % | | | | | |
| Période SysTick | 1 ms ± 1 % | | | | | |
| Vitesse à 25 / 50 / 75 / 100 % (avant) | croissante, stable ± 10 % | | | | | |
| Vitesse à 25 / 50 / 75 / 100 % (arrière) | idem | | | | | |
| Déphasage E_A / E_B (avant, arrière) | quadrature, inversé selon le sens | | | | | |
| Délai E-Stop → PWM nulle | < 1 ms | | | | | |
| Durée d'un bip | 100 ms ± 10 % | | | | | |

## Tableau des essais (T1 à T10)

| Essai | Date | Résultat observé | Verdict | Preuve (fichier) |
|---|---|---|---|---|
| T1 Réinitialisation | | | | |
| T2 Cycle User et sens | | | | |
| T3 PWM | | | | |
| T4 Rampe | | | | |
| T5 Encodeur | | | | |
| T6 Vitesse | | | | |
| T7 E-Stop | | | | |
| T8 Urgence et acquittement | | | | |
| T9 Buzzer | | | | |
| T10 SysTick et robustesse | | | | |

## Routine conservée pour L3-A
- Routine (`button_pressed`, `led_set`, `motor_set_pwm` ou `encoder_read`) :
- Interface :
- Cas d'essai et résultats :

## Déclaration des sources et de l'usage d'outils d'IA générative
- Sources (dont le complément de démarrage et, le cas échéant, le corrigé du laboratoire 1) :
- Outils d'IA (outil, version, usage) ou « aucun usage » :

