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

