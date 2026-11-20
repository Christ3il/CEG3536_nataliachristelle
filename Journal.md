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

# JOURNAL.md — Journal d'équipe, CEG 3536, laboratoire 3 (automne 2026)

Équipe : `Natalia Proano` et `Christelle Ilunga` — Section : `A01` — Dépôt Git : `<adresse>`

## Jalon J2 — module d'événements testé sur hôte

| Plateforme | Compilateur et version | Commande | Résultat (cas réussis / échecs) | Date et validation Git |
|---|---|---|---|---|
| Windows | | `make` dans `hote/` |Cas1: Réussi Cas2:Réussi Cas3: Réussi Cas4 Reussi Cas5: Réussi Cas6:Réussi Cas7: Réussi Cas8 Reussi Cas 9:Réussi | |
| Linux | |Cas 1: Réussi | Cas1: Réussi Cas2:Réussi Cas3: Réussi Cas4 Reussi Cas5: Réussi Cas6:Réussi Cas7: Réussi Cas8 Reussi Cas 9:Réussi| |
| STM32 (cible) | arm-none-eabi-gcc | commande série `q` | | |

Cas ajoutés par l'équipe (au-delà des 9 fournis) :

| Cas | Description | Résultat |
|---|---|---|
| 10 | | |

Différences observées entre hôtes (tailles des types, options, avertissements) :

## Rôles et rotation

| Séance | Réalise | Valide | Module C écrit par chacun | Routine assembleur écrite ou modifiée par chacun |
|---|---|---|---|---|
| Séance 1 | | | | |
| Période d'étude | | | | |
| Séance 2 | | | | |

## Calculs préalables

| Grandeur | Formule | Valeur | Vérifiée par |
|---|---|---|---|
| `RPM_Q16_K` | round(240 × 65 536 / 748) |21028 | T3 |
| Erreur relative de la constante | (k − 240 × 65 536 / 748) / (240 × 65 536 / 748) |0,0019 % (0,0000193) | T3 |
| fronts maximal sans débordement | 2³² / k |204 249 | T3 |
| `LPUART1_BRR` | 256 × 4 000 000 / 115 200 |8889 (0x22B9) | T9 |
| Débit ADC par voie | 4 MHz / (2 × (640,5 + 12,5)) |3,06 kHz (3 063 Hz) | T4 |
| Durée d'un tour du tampon DMA | 16 / débit par voie |5,22 ms | T4 |
| Résolution de la température | 3 300 mV / 4 095 / 10,9 mV/°C | 0,074 °C (par compte)| T6 |

## Étalonnage de la température (E6)

| Mesure | Température de référence (°C) | `temp_mv` lu | `TEMP_MV_REF` / `TEMP_C10_REF` retenus | Position de S2 |
|---|---|---|---|---|
| Ambiante | | | | |
| Capteur tenu entre deux doigts (30 s) | | | | |
| Conditionnement externe (pont OUT–IN ou circuit) | | | | |

Analyse interne / externe (plage, résolution, bruit) :

## Journal des séances

### Séance 1 — `7 nov` — réalise : `Natalia` / valide : `Christelle`
- Objectifs :mise en œuvre, Projet qui compile en C + assembleur; véhicule fonctionnel comme au laboratoire 2 à partir de main.c; calculs consignés.
- Fait :
- Décisions (découpage des modules, format des trames, routine L3-A choisie) : Motor set pwm
- Difficultés et solutions :
- Mesures :
- Validations Git :

### Période d'étude — travail sur hôte
- Fait (evq, test_evq, cas ajoutés, L3-B / L3-C rédigés) :
- Validations Git :

### Séance 2 — `14 nov` — réalise : `Christelle` / valide : `Natalia`
- Objectifs :achèvement et démonstration, Toutes les exigences démontrées; J2 validé; fiches périphériques « ADC/DMA » et « LPUART1 » remplies; démonstration validée en présence des deux membres.
- Fait :
- Décisions :
- Difficultés et solutions :
- Mesures (température, cycles DWT, désassemblage) :
- Validations Git :

## Composante L3-A : comparaison assembleur / C

Routine comparée : `<motor_set_pwm>`

| Cas | Entrée | Résultat assembleur | Résultat C | Effet de bord (registre / variable) | Écart |
|---|---|---|---|---|---|
| 1 | 0|0 |0 | `TIM1->CCR1 = 0`|0 |
| 2 |25 |50 |50 |`TIM1->CCR1 = 50` |0 |
| 3 |50|100 |100 |`TIM1->CCR1 = 100` |0 |
| 4 | 75|150 |150 |`TIM1->CCR1 = 150` | 0|
| 5 | 100|200 |200 |`TIM1->CCR1 = 200` | 0|
| 6 |150(saturé)|200 |200 | `TIM1->CCR1 = 200`| 0|


| Version | Cycles DWT (moyenne) | Taille (octets) | Registres utilisés | Observations (prologue, volatile) |
|---|---|---|---|---|
| Assembleur | ~12 cycles | 28 octets | r0, r1, r2 | Routine feuille, pas de prologue/épilogue, code optimisé à la main |
| C, -O0 | ~34 cycles | ~64 octets | r0, r1, r2, r3, sp | Prologue/épilogue complets, empilement sur la pile, appels intermédiaires |
| C, -O2 | ~8 cycles | ~24 octets | r0, r1, r2 | Inline/optimisé par le compilateur, suppression des empilements superflus |

## Composante L3-C : objet d'acquisition

- Version 1 (validation Git) :
- Version 2 (validation Git) et ce qui a changé :
- Essai d'indépendance des deux instances :
- Comparaison avec la version impérative (annexe) :
- Limites :

## Composante L3-D : traces

| Élément | Preuve (fichier) |
|---|---|
| Désassemblage -O0 annoté | |
| Désassemblage -O2 annoté | |
| Trois instructions et leur encodage Thumb | |
| Captures du débogueur (R0–R3, SP, variable volatile) | |
| Cycles DWT -O0 / -O2 et transformation analysée | |

## Tableau des essais (T1 à T10)

| Essai | Date | Résultat observé | Verdict | Preuve (fichier) |
|---|---|---|---|---|
| T1 Initialisation en C | | | | |
| T2 Appel C → assembleur | | | | |
| T3 Virgule fixe | | | | |
| T4 ADC et DMA | | | | |
| T5 Consigne | | | | |
| T6 Température | | | | |
| T7 File d'événements | | | | |
| T8 E-Stop | | | | |
| T9 Télémétrie | | | | |
| T10 Comparaison et traces | | | | |

## Déclaration des sources et de l'usage d'outils d'IA générative
- Sources (complément, corrigé du laboratoire 2 le cas échéant, CMSIS, manuel) :
- Outils d'IA (outil, version, usage) ou « aucun usage » :





# JOURNAL.md — Journal d'équipe, CEG 3536, projet final (automne 2026)

Équipe : `<Natalia>` et `<Christelle>` — Section : `A01` — Dépôt Git : `<adresse>`
— Variante L4-A attribuée : `0` — Journal du laboratoire 3 : `JOURNAL_Lab3.md`

# Partie I

## Partie I — Rôles et rotation

| Séance | Réalise | Valide | Pilote I²C écrit par chacun | Pilote SPI ou routine assembleur de chacun |
|---|---|---|---|---|
| Séance 1 | | | | |
| Entre les séances | | | | |
| Séance 2 | | | | |

## Partie I — Calculs préalables

| Grandeur | Formule | Valeur | Vérifiée par |
|---|---|---|---|
| Pas de l'horloge I²C | (PRESC + 1) / 4 MHz | | T1 |
| SCL bas / SCL haut | (SCLL + 1) × pas / (SCLH + 1) × pas | | T1 |
| Fréquence SCL (avec les délais de synchronisation) | | | T1 |
| `TIMINGR` retenu | | | T1 |
| Durée d'une écriture de deux octets de données | 27 bits / fréquence SCL | | T1 (DWT) |
| Débit SPI | PCLK2 / 2^(BR + 1) | | T7 |
| Pire cas de réécriture du LCD | 32 caractères × (position + caractère) × 1 tick | | T3 |
| Transactions I²C par seconde au repos | | | T10 |

## Partie I — Relevés des modules

| Module | Relevé | Valeur | Preuve (fichier) |
|---|---|---|---|
| Bus I²C | Adresses trouvées par `i2c_scan` | | |
| Bus I²C | `GPIOF->IDR` bits 0 et 1 au repos ; `I2C2->ISR` après une transaction | | |
| Extenseur des DEL | Octet écrit pour allumer Y1 seule ; R4 seule | | |
| Extenseur des commutateurs | Octet lu au repos ; SW1 enfoncé ; SW8 enfoncé | | |
| LCD | Octets de commande confirmés (fonction, allumage, effacement, mode) | | |
| Rétroéclairage | Registres rouge / vert / bleu confirmés | | |
| TouchPad | Front actif de THI ; `0x5E` relu après `tp_init` ; deux seuils relus | | |
| Capteur environnemental | Identifiant lu ; page utilisée pour chaque registre | | |
| Capteur environnemental | Température / humidité / pression au repos ; écart avec le capteur analogique | | |
| PIR | Durée du niveau haut ; `pir_t_ms` de deux fronts successifs | | |

Table des touches (électrode → touche), relevée au débogueur :

| Électrode | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Touche | | | | | | | | | | | | |

## Partie I — Essais hôte (E11)

| Plateforme | Compilateur et version | `test_evq` (réussis / échecs) | `test_tableau` (réussis / échecs) | Date et validation Git |
|---|---|---|---|---|
| Windows | | | | |
| Linux | | | | |
| STM32 (cible) | arm-none-eabi-gcc | commande `q` : | commande `f` : | |

Cas ajoutés à `tableau_test.c` (au-delà des 6 fournis) :

| Cas | Description | Résultat |
|---|---|---|
| 7 | | |

## Partie I — Banc de `trame_xor8` (T9)

| Cas | Attendu | Obtenu | Verdict |
|---|---|---|---|
| Chaîne vide | 0x00 | | |
| « A » | 0x41 | | |
| « T,0 » | 0x48 | | |
| « 123456789 » | 0x31 | | |
| Octets 0x00 à 0xFF | 0x00 | | |

## Partie I — Journal des séances

### Séance 1 — `<date>` — réalise : `<nom>` / valide : `<nom>`
- Objectifs :
- Fait :
- Décisions (découpage, répartition du bus, format des lignes) :
- Difficultés et solutions :
- Mesures :
- Validations Git :

### Entre les séances — travail sur hôte
- Fait (tableau.c, test_tableau, fsm.c, lecture de l4a_defaut.c) :
- Validations Git :

### Séance 2 — `<date>` — réalise : `<nom>` / valide : `<nom>`
- Objectifs :
- Fait :
- Décisions :
- Difficultés et solutions :
- Mesures (capteur, PIR, télémétrie, L4-A) :
- Validations Git :

## Partie I — Composante L4-A : diagnostic d'un défaut TouchPad/I²C

Variante : `<n>` — validation Git de la version défectueuse : — de la version corrigée :

1. Symptôme (attendu, observé, conditions de reproduction) :

2. Hypothèses, classées avant toute mesure :

| Rang | Hypothèse | Niveau (lignes et broches / adressage et protocole / configuration du composant / interruption et garde) | Ce qu'on observerait si elle était vraie |
|---|---|---|---|
| 1 | | | |
| 2 | | | |
| 3 | | | |

3. Mesures :

| Hypothèse visée | Mesure (registre, balayage, relecture, compteur) | Résultat | Preuve (fichier) |
|---|---|---|---|
| | | | |

4. Essai discriminant — prédiction écrite **avant** l'essai (date et heure) :

   Résultat de l'essai :

5. Interprétation (hypothèses écartées, hypothèse retenue, pourquoi) :

6. Correction et non-régression (les 12 touches, la garde Touch En) :

7. Conclusion et limites (ce qui est démontré, ce qui est supposé, ce qui reste à vérifier) :

## Partie I — Table des états et des priorités (en vue du jalon J3)

| État | Événement (par priorité décroissante) | Condition | État suivant | Sorties (moteur, DEL, avertisseur, LCD) |
|---|---|---|---|---|
| ARRÊT | | | | |
| MARCHE_AVANT | | | | |
| MARCHE_ARRIÈRE | | | | |
| ARRÊT_URGENCE | | | | |
| ARRÊT_ÉVÉNEMENT | | | | |

Priorités des interruptions (valeur, justification) : E-Stop — encodeur — SysTick — PIR — THI —

## Partie I — Tableau des essais (T1 à T10)

| Essai | Date | Résultat observé | Verdict | Preuve (fichier) |
|---|---|---|---|---|
| T1 Bus I²C et balayage | | | | |
| T2 Extenseurs | | | | |
| T3 LCD et rétroéclairage | | | | |
| T4 TouchPad et garde | | | | |
| T5 Commandes du TouchPad | | | | |
| T6 PIR | | | | |
| T7 Capteur environnemental | | | | |
| T8 Événements et priorités | | | | |
| T9 Télémétrie contrôlée | | | | |
| T10 Robustesse et non-régression | | | | |

# Partie II

## Partie II — Rôles et rotation

| Période | Réalise | Valide | Module sans matériel de chacun | Routine assembleur ou intégration de chacun |
|---|---|---|---|---|
| Entre les séances 1 et 2 (prise en main de l'outil) | | | | |
| Séance 2 (24 / 27 nov.) | | | | |
| Jalon J3 (27 nov.) | | | | |
| Entre les séances 2 et 3 | | | | |
| Séance 3 (1er / 4 déc.) | | | | |
| Démonstration finale (4 / 8 déc.) | | | | |

## Partie II — Calculs préalables

| Grandeur | Formule | Valeur | Vérifiée par |
|---|---|---|---|
| Fronts par fenêtre à 100 tr/min | 100 × 748 / 600 | | T14 |
| Résolution de la vitesse à 100 tr/min | 1 front / fronts par fenêtre | | T14 |
| Constante Q16.16 de la fenêtre de 100 ms | 600 × 65 536 / 748, arrondie | | banc du lab. 3 |
| Fronts du trajet de référence | 105 × 748 | | T13 |
| Durée prévue du trajet de référence | somme des tours / (tr/min / 60) | | T13 |
| Commande initiale du régulateur à 150 tr/min | 150 × 100 / 340 | | T14 |
| Durée de masquage admise | 200 cycles / 4 MHz | | T11 |
| Occupation de la file au pire cas prévu | | | T11 |

## Partie II — Automate (L5-B)

| Date | Version de la table (somme) | Résultat du vérificateur | Erreurs et contre-exemples | Correction |
|---|---|---|---|---|
| | | | | |

Invariants imposés et ajoutés par l'équipe :

| Invariant | Type | Pourquoi | Résultat |
|---|---|---|---|
| | | | |

Version fautive conservée : fichier `…`, validation Git `…`, contre-exemple :

```
(copier ici le contre-exemple produit par l'outil)
```

Correspondance entre les événements de la file et les entrées du modèle
(traduction faite dans `fsm.c`) :

| Événement, garde | Entrée du modèle |
|---|---|
| | |

Comparaison des traces (au moins trois séquences) :

| Séquence | Pas | Hôte Windows | Hôte Linux | Cible (commande `g`) |
|---|---|---|---|---|
| | | | | |

## Partie II — File d'événements et sections critiques (L5-A)

| Question | Réponse de l'équipe | Preuve |
|---|---|---|
| Producteurs (gestionnaires) et consommateur | | |
| Instructions placées dans la section critique | | |
| Politique de débordement retenue, et pourquoi | | |
| Mécanisme de garantie pour E-Stop et défaut | | |
| `crit_autotest` (commande `c`) : cas réussis | | |
| `crit_max_cycles` relevé (repos, scénario S3, rafale) | | |
| `evq_max` relevé (repos, scénario S3, rafale) | | |
| Rafale `e` : événements acceptés, refusés, consommés | | |
| Délai de E-Stop pendant une rafale | | |

## Partie II — Réglage du régulateur

Consigner chaque essai, y compris ceux qui échouent : c'est la justification
des gains retenus.

| Essai | Kp (Q8) | Ki (Q8) | Consigne (tr/min) | Vitesse à 2 s | Erreur (%) | Dépassement | Observation |
|---|---|---|---|---|---|---|---|
| 1 | 26 | 26 | | | | | |
| | | | | | | | |

Gains retenus : Kp = `…`, Ki = `…` — raison :

## Partie II — Relevés de la partie II

| Essai | Relevé | Valeur | Preuve (fichier) |
|---|---|---|---|
| T13 | Distance aux changements de segment (20, 60, 75) et à la fin (105) | | |
| T13 | Reprise après un arrêt au feu rouge : distance avant / après | | |
| T14 | Erreur 2 s après chaque changement de consigne (quatre segments) | | |
| T14 | Plafond abaissé pendant S2 : commande et vitesse | | |
| T15 | Délai entre la commande `s` et l'état DÉFAUT | | |
| T15 | Délai entre la commande `n` et l'état DÉFAUT | | |
| T16 | Limitation à 42,0 °C ; arrêt à 52,0 °C ; sortie à 25,0 °C | | |
| T18 | Initialisation : durée de INIT, ressources vérifiées | | |
| T18 | Démarrage avec un module absent (commande `d`) | | |

## Partie II — Portage (L5-C)

| | Windows x86-64 | Linux x86-64 | STM32 |
|---|---|---|---|
| Compilateur et version | | | |
| Options | | | |
| Tailles : `int`, `long`, pointeur, `size_t` | | | |
| Fichiers remplacés (couche d'adaptation) | | | |
| `test_evq` / `test_tableau` | | | |
| `test_trajet` / `test_regul` / `test_surv` | | | |
| `test_automate` (traces) | | | |
| Rejeu de la trace du scénario `…` | | | |
| Rejeu de la trace du scénario `…` | | | |

Différences observées et explication :

## Partie II — Décision collective et désaccord (L5-D)

Décision technique prise en équipe :

| Élément | Contenu |
|---|---|
| Question à trancher | |
| Options envisagées | |
| Critères | |
| Choix et raison | |
| Résultat observé après coup | |

Désaccord (réel, ou scénario de `dossier/scenario_desaccord.md`) :

| Élément | Contenu |
|---|---|
| Objet du désaccord | |
| Position de chacun | |
| Démarche suivie | |
| Issue | |

## Partie II — Séances

### Séance 2 — date : `…`

- Objectifs :
- Réalisé :
- Problèmes rencontrés, hypothèses, essais :
- Validations Git (auteur, identifiant, objet) :
- À faire avant la séance 3 :

### Entre les séances 2 et 3

- Réalisé :
- Validations Git :

### Séance 3 — date : `…`

- Objectifs :
- Réalisé :
- Problèmes rencontrés, hypothèses, essais :
- Validations Git :
- À faire avant la démonstration finale :

### Démonstration finale — date : `…`

- Scénarios S1 à S5 : résultat de chacun
- Questions posées et réponses à approfondir dans le rapport :

## Vidéo de présentation (énoncé, section 7.2)

Durée visée : 7 à 10 minutes. Filmer les scénarios dès qu'ils fonctionnent, sans attendre la veille de la remise.

| Séquence | Durée prévue | Qui parle | Ce qui est montré (véhicule, afficheur, télémétrie, code) | Tournée le |
|---|---|---|---|---|
| Présentation de l'équipe, du véhicule et de l'architecture | 1 min | | | |
| Démonstration : conduite manuelle, trajet autonome, arrêt et reprise, E-Stop, défaut injecté | 4 min | | | |
| Explication technique du membre A : `…` | 1 min 30 | | | |
| Explication technique du membre B : `…` | 1 min 30 | | | |
| Bilan : limites, ce qui serait fait autrement | 1 min | | | |

Durée finale : `…` — fichier ou lien : `…` — outils de montage : `…`

## Sources et outils

| Source ou outil | Usage |
|---|---|
| Compléments du laboratoire 4 et du projet | |
| Outil `automate.py` | |
| Corrigé du laboratoire 3 (le cas échéant) | |
| Fiches techniques, manuel | |
| Outils d'IA générative (outil, version, usage) ou « aucun usage » | |
