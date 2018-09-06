# Toxic Comment Classification Challenge

https://www.kaggle.com/c/jigsaw-toxic-comment-classification-challenge

L’objectif de ce challenge est de détecter la toxicité de commentaires, suivant différents niveaux ("toxic", "severe_toxic", "obscene", "threat", "insut", "identity_hate"). 

Le fichier "Data_exploration.ipynb" présente quelques analyses exploratoires des données, afin de mieux en comprendre la nature.
On observe qu'il s'agit d'un problème de classification multi-classe, puisque qu'un commentaire peut posséder de multiples étiquettes (labels).

L'approche présentée vise à traiter ce problème de classification de textes à l'aide de réseaux de neurones. De nombreux travaux ont démontré l’efficacité des réseaux de neurones pour la classification et l’analyse textuelle. Dans le but de fournir une solution simple, les modèles qui ont été définis sont des modèles convolutifs. 

La première réalisation est présentée dans le fichier "Toxic Commment Classification.ipynb". Elle recourt a des embeddings de type GloVe, et s'appuie sur une architecture de modèle simple, basée sur des convolutions 1D. La soumission des résultats de cette solution a permis d'obtenir un score de 0,9517.

J'ai ensuite repris le même modèle, mais en utilisant cette fois les embeddings fastText. Cette solution est présentée dans le fichier "Toxic Comment Classification-V2-FastText.ipynb". L’avantage de FastText est qu’il prend comme plus petite entité des n-grams du mot, contrairement à Word2Vec / Glove qui ne prennent que le mot. Ainsi, FastText est plus robuste pour les mots inconnus et les variations morpologiques. La soumission des résultats de cette solution a permis d'obtenir un meilleur score, de 0,9679.

Enfin, le fichier "Toxic Comment Classification-V3-FastText-Conv2D.ipynb" présente une solution s'appuyant sur une architecture de modèle basée sur des convolutions 2D. Les embeddings fastText sont aussi utilisés. Le recours aux convolutions 2D pour la classification de textes est référencé dans l'état de l'art (cf article : Yoon Kim, 2014, Convolutional neural networks for sentence classification, arXiv preprint arXiv:1408.5882 (2014)). La soumission des résultats de cette solution a permis d'obtenir un score de 0,9756.

Notons que l'on peut envisager une (légère) amélioration des performances de classification en ayant recours à des couches récurrentes / LSTM. Cependant, l'objectif étant ici de fournir une solution simple et efficace, cette solution n'a ici pas été mise en oeuvre, car 
plus coûteuse en termes de ressources et de temps de calcul. Le choix des convolutions permet donc d’obtenir un bon compromis entre performances statistiques et efficacité (temps, ressources informatiques).

Aussi, un point d'amélioration pouvant être envisagé consisterait à traiter les apostrophes, ce qui n'a pas été fait dans les solutions présentées.
