# Synthèse des expériences de sélection de la baseline

Les expériences exploratoires sont archivées dans [experiments_baseline.ipynb](../notebooks/experiments_baseline.ipynb). Les valeurs ci-dessous sont les sorties communiquées depuis Colab, arrondies à quatre décimales.

| Modèle | F1 macro CV structurelle | F1 train | Gap | Coefficients non nuls moyens |
|---|---:|---:|---:|---:|
| L2 C=1 | .7987 | .9532 | .1545 | 50437 |
| L2 C=10 | .8106 | .9836 | .1730 | 50437 |
| L2 C=5 | .8101 | .9777 | .1676 | 50437 |
| Elastic Net C=10 | .8108 | .9870 | .1762 | 34568 |
| Elastic Net C=1 | .8024 | .9217 | .1192 | 12157 |
| L1 C=1 | .8006 | .8939 | .0932 | 2704 |
| L1 C=10 | .7981 | .9912 | .1931 | 10619 |
| Max features 50000 | .8101 | .9832 | .1731 | 50000 |
| Max features 25000 | .8061 | .9653 | .1593 | 25000 |
| Max features 10000 | .7959 | .9339 | .1380 | 10000 |
| Max features 5000 | .7808 | .9025 | .1217 | 5000 |
| Chi2 25000 | .7981 | .9534 | .1553 | 25000 |
| Chi2 10000 | .7863 | .9136 | .1273 | 10000 |
| L2 C=0.5 | .7926 | .9362 | .1436 | 50437 |
| L2 C=0.1 | .7451 | .8424 | .0973 | 50437 |

La règle initiale d'une erreur standard retenait L2 C=5 (seuil .808971). La décision ultérieure privilégie L1 C=1 pour sa parcimonie et son gap moindre : changement explicite du critère, effectué après inspection de la CV structurelle. L1 n'est pas le meilleur modèle en F1 et son score officiel n'est pas encore mesuré. Les scores de CV après sélection sont exploratoires. La validation officielle a déjà été consultée pour les baselines L2 et n'est donc pas un test entièrement aveugle.

Diagnostic : 8527 arbres Stanford, 58610 correspondances uniques, 4031 multiples, 4708 absentes. Une composante géante regroupe 61267 lignes. La CV par arbres avec purge et validation sur racines réduit l'optimisme apparent, mais modifie aussi la quantité et la nature des données. Les courbes d'apprentissage L2 montrent un gap persistant. Aucun test sur les labels officiels masqués n'a été effectué.

Références : Socher et al. (2013), https://aclanthology.org/D13-1170/ ; Wang et Manning (2012), https://aclanthology.org/P12-2018/ ; https://www.statlearning.com/resources-python ; https://scikit-learn.org/stable/modules/learning_curve.html .
