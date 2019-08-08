# Random-Forests
Built Node and Decision Tree classes from the ground-up using the Cross-Entropy Loss and a recursive `grow-tree` function. 

Built a Random Forests class from the ground-up, which instantiates and trains many decision trees.

Tested model on SPAM dataset and TITANIC dataset. Accuracies were:
Titanic Dataset:
		Decision Tree:
			Training accuracy: 0.84779
			Validation accuracy: 0.756
		Random Forest (7 trees): 
			Training accuracy: 0.84646
			Validation accuracy: 0.78
	Spam Dataset:
		Decision Tree:
			Training accuracy: 0.801237
			Validation accuracy: 0.80355
		Random Forest (7 trees): 
			Training accuracy: 0.82108
			Validation accuracy: 0.79969
	Kaggle Scores: (username: Adish Jain)
		Titanic: 0.83870 (using Random Forest with 7 trees)
		Spam: 0.78258 (using Decision Tree)



In the Titanic dataset, for categorical features, I used a one-hot encoding strategy to remove the categories and replace them with numerical values. For missing values, I 	replaced all NaN’s with the mean value (for the age column). Additionally, features like 	cabin number and ticket number were removed from the dataset in the preprocessing step.

My stopping criterion were two: if my decision tree had reached some specified 	maxdepth, then I stopped the growth of the tree by producing a Leaf node with the mode 	value. Otherwise, if a node was pure (all labels were of the same class), I also stopped 	growing the tree and produced a Leaf node with that single class label.

I implemented RandomForests by initializing a RandomForest instance with some 	specific variables like numTrees (which would be the number of trees in the forest), 	maxdepth (the max depth of each tree), numFeatures (the size of the subset of random 	features which would be considered on each split). To fit the RandomForest model on the 	training data, I, one time for each tree, created a bootstrapped version of the design 	matrix, instantiated a decision tree, and fit the decision tree to the bootstrapped training 	data. (I also changed my segmenter function in my decision tree to account for the 	numFeatures hyperparameter). Finally, to predict from my model, I went through each 	tree I had trained, and looked at their predictions on the test data, and took a majority 	vote across all the trees to come up with a final prediction result. 
