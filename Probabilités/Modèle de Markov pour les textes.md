# Exemple

Un **modèle de Markov pour les textes** engendre un texte comme une suite de symboles (lettres ou mots) selon une [[Chaîne de Markov d'ordre N]] : chaque symbole est tiré conditionnellement aux $N$ symboles précédents ($N = 0$ correspond à des symboles tirés indépendamment les uns des autres). Les séquences suivantes sont des textes engendrés de cette façon.

## Approximation de Markov du langage

- **Ordre 1** : REPRESENTING AND SPEEDILY IS AN GOOD APT OR COME CAN DIFFERENT NATURAL HERE HE THE A IN CAME THE TO OF TO EXPERT GRAY COME TO FURNISHES THE LINE MESSAGE HAD BE T
- **Ordre 2** : THE HEAD AND IN FRONTAL ATTACK ON AN ENGLISH WRITER THAT THE CHARACTER OF THIS POINT IS THEREFORE ANOTHER METHOD FOR THE LETTERS THAT THE TIME OF WHO EVER TOLD THE PROBLEM FOR AN UNEXPECTED

## Approximation de Markov des mots

- **Ordre 0** : XFOML RXKXRJFFUJ ZLPWCFWKCYJ FFJEYVKCQSGHYD QPAAMKBZAACIBZLHJQD
- **Ordre 1** : OCRO HLI RGWR NWIELWIS EU LL NBNESEBYA TH EEI ALHENHTTPA OOBTTVA NAH RBL
- **Ordre 2** : ON IE ANTSOUTINYS ARE T INCTORE ST BE S DEAMY ACHIN D ILONASIVE TUCOOWE AT TEASONARE FUSO TIZIN ANDY TOBE SEACE CITSBE
- **Ordre 3** : IN NO IST LAT WHEY CRATICT FROURE BIRS GROCID PONDENOME OF DEMONSTURES OF THE REPTABIN IS REGOACTIONA OF CRE
- **[[Champ aléatoire de Markov]]** à 1000 « caractéristiques », sans « machine » sous-jacente (Della Pietra et al.) : WAS REASER IN THERE TO WILL WAS BY HOMES THING BE RELOVERATED THER WHICH CONISTS AT RORES ANDITING WITH PROVERAL THE CHESTRAING FOR HAVE TO INTRALLY OF QUT DIVERAL THIS OFFECT INATEVER THIFER CONSTRANDED STATER VILL MENTTERING AND OF IN VERATE OF TO

# Remarque

Les séquences ci-dessus sont des textes aléatoires : elles reproduisent des enchaînements de lettres ou de mots de la langue, sans former de phrases réellement sensées.
