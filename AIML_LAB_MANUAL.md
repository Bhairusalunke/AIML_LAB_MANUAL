# AIML LAB MANUAL

Maharashtra Institute of Technology
Chhatrapati Sambhajinagar
(An Autonomous Institute)

Faculty of Science & Technology
Syllabus of Final Year B. Tech (Electronics and Computer Engineering) (Semester VII)
WEF 2026-27 (NEP 2020 Based Curriculum)

Course Category: PCC
Course Code: ECE422
Course: Artificial Intelligence and Machine Learning Lab
Teaching Scheme:
Practical: 2 Hrs./week

---

## Table of Contents

1. Cover Page
2. Certificate / Approval Page
3. Declaration Page
4. Acknowledgements
5. Table of Contents
6. Syllabus and Course Overview
   - Prerequisite
   - Objectives
   - List of Practicals
   - List of Equipment/Software
7. Practical 1: Implementation of Uninformed Search Algorithms (BFS, DFS)
8. Practical 2: Implementation of Informed Search Algorithms (A*, memory-bounded A*)
9. Practical 3: Find a goal by Deepening Depth First Search (DFID)
10. Practical 4: Predicting house prices by Linear Regression
11. Practical 5: K Nearest Neighbour (KNN) classification of Iris dataset
12. Practical 6: Build decision trees and random forests
13. Practical 7: Implement naïve Bayes models
14. Practical 8: Clustering data by K-means clustering algorithm
15. Practical 9: Implementing ensembling techniques
16. Practical 10: Build SVM models
17. Grading & Evaluation / CAPT tables
18. Rubric for Practical Assessment
19. Appendix A: Sample datasets and download links
20. Appendix B: Suggested reading and references
21. Appendix C: Lab safety and policy
22. Blank code pages placeholders (one per practical)
23. Bibliography

---

## Syllabus and Course Overview

### Prerequisite
Basic Programming Knowledge, Mathematics Fundamentals, Basic Computer Science Concepts, Introductory Knowledge of Graphs.

### Objectives
- Study about uninformed and heuristic search techniques.
- Learn techniques for reasoning under uncertainty.
- Introduce Machine Learning and supervised learning algorithms.
- Study ensembling and unsupervised learning algorithms.
- Learn the basics of deep learning using neural networks.

### List of Practicals
1. Implementation of Uninformed search algorithms (BFS, DFS)
2. Implementation of Informed search algorithms (A*, memory-bounded A*)
3. Find a goal by Deepening Depth First Search (DFID) algorithm
4. Predicting house prices by Linear Regression
5. K Nearest Neighbour (KNN) classification of Iris dataset
6. Build decision trees and random forests
7. Implement naïve Bayes models
8. Clustering data by K-means clustering algorithm
9. Implementing ensembling techniques
10. Build SVM models

### List of Equipment / Instruments
1. Computer Systems / Workstations
2. Programming Environment (Python with IDEs like Jupyter Notebook / VS Code / PyCharm)
3. AI & ML Software Libraries (NumPy, Pandas, Scikit-learn, Matplotlib, TensorFlow / PyTorch)
4. Networking Facility (LAN / Internet for downloading libraries, datasets, and collaboration)

---

# Practical Format (applies to every practical)
Each practical in this manual follows the exact structure below and is formatted for clarity and professional presentation. All text should be typeset in Times New Roman, 12 pt, and justified when converted to Word or PDF.

- Aim
- Objectives
- Software Required
- Theory
- Algorithm (pseudocode)
- Flowchart (diagram placeholder)
- Code Page: One full blank page reserved for code (approx. 40 blank lines)
- Conclusion
- CAPT (Continuous Assessment Practical Test) evaluation table

---

# Practical 1: Implementation of Uninformed Search Algorithms (BFS, DFS)

Aim
To implement Breadth First Search (BFS) and Depth First Search (DFS) algorithms and analyze their performance on example search problems.

Objectives
1. Understand the working of BFS and DFS.
2. Implement BFS and DFS in Python.
3. Measure time and space requirements of both algorithms on sample graphs.
4. Compare completeness and optimality properties.

Software Required
- Python 3.8+
- Jupyter Notebook or VS Code
- Libraries: networkx, matplotlib, numpy, pandas

Theory
Uninformed search algorithms explore the search space without additional information about goal proximity. BFS explores level by level guaranteeing the shortest path (in terms of number of edges) for unweighted graphs; DFS explores by diving deep along a path before backtracking and generally has lower memory requirements but may not be complete for infinite-depth spaces.

Key properties:
- BFS: Complete (if branching factor finite), Optimal for uniform-cost by edges, Time complexity O(b^d), Space complexity O(b^d)
- DFS: Not guaranteed complete for infinite depth (without depth limit), Time complexity O(b^m), Space O(bm)

Algorithm (pseudocode)

Breadth-First Search (BFS)
1. procedure BFS(start, goal)
2.     initialize queue with start
3.     visited = set(start)
4.     while queue not empty:
5.         node = dequeue(queue)
6.         if node == goal: return path_to(node)
7.         for each neighbor in expand(node):
8.             if neighbor not in visited:
9.                 add neighbor to visited
10.                enqueue neighbor
11.    return failure

Depth-First Search (DFS) — iterative
1. procedure DFS(start, goal)
2.    initialize stack with start
3.    visited = set(start)
4.    while stack not empty:
5.        node = pop(stack)
6.        if node == goal: return path_to(node)
7.        for each neighbor in expand(node):
8.            if neighbor not in visited:
9.                add neighbor to visited
10.               push neighbor
11.   return failure

Flowchart
[Flowchart placeholder — in the Word/PDF will be inserted as a clean diagram matching the sample manual style.]

Code Page
[This page is reserved for student code. Insert approximately 40 blank lines in the Word file for students to type/paste code during lab.]

Conclusion
Students will understand search strategies, implement BFS and DFS, and assess trade-offs between memory usage and completeness. They will be able to select suitable uninformed search strategies for specific problem constraints.

CAPT Evaluation Table
| Item                          | Max Marks |
|-------------------------------|-----------|
| Aim & Objectives              | 5         |
| Algorithm & Flowchart         | 10        |
| Program Implementation (Code) | 25        |
| Output & Analysis             | 15        |
| Report & Viva                 | 10        |
| Total                         | 65        |

---

# Practical 2: Implementation of Informed Search Algorithms (A*, memory-bounded A*)

Aim
To implement informed search strategies (A* and memory-bounded A*) and evaluate their efficiency compared to uninformed methods.

Objectives
1. Understand heuristic search principles.
2. Implement A* search with admissible heuristics.
3. Explore memory-bounded variants such as IDA* or SMA*.
4. Compare path optimality and performance metrics.

Software Required
- Python 3.8+
- Jupyter Notebook / VS Code
- Libraries: heapq (built-in), numpy, networkx, matplotlib

Theory
Informed search algorithms use heuristics to guide the search towards the goal. A* maintains f(n) = g(n) + h(n) where g(n) is the path cost and h(n) is the heuristic estimate of remaining cost. With an admissible and consistent heuristic, A* is optimal.

Algorithm (pseudocode)
A* Search
1. procedure A_Star(start, goal, h)
2.    open = priority_queue with start (priority f=start.g + h(start))
3.    came_from = map()
4.    g_score[start] = 0
5.    while open not empty:
6.        current = pop lowest f from open
7.        if current == goal: return reconstruct_path(came_from, current)
8.        for neighbor in neighbors(current):
9.            tentative_g = g_score[current] + cost(current,neighbor)
10.           if tentative_g < g_score.get(neighbor, inf):
11.               came_from[neighbor] = current
12.               g_score[neighbor] = tentative_g
13.               f = tentative_g + h(neighbor)
14.               push/update neighbor in open with priority f
15.   return failure

Flowchart
[Flowchart placeholder — graphical diagram to be inserted in the DOCX/PDF.]

Code Page
[Reserved blank page for code — ~40 blank lines]

Conclusion
Students will apply heuristics and implement A*, understanding trade-offs between heuristic strength and performance. They will also explore memory-bounded adaptations useful in constrained environments.

CAPT Evaluation Table
| Item                          | Max Marks |
|-------------------------------|-----------|
| Aim & Objectives              | 5         |
| Algorithm & Flowchart         | 10        |
| Program Implementation (Code) | 25        |
| Output & Analysis             | 15        |
| Report & Viva                 | 10        |
| Total                         | 65        |

---

# Practical 3: Find a goal by Deepening Depth First Search (DFID)

Aim
To implement the Depth-Limited and Iterative Deepening DFS (DFID) algorithms and analyze their use cases.

Objectives
1. Implement depth-limited DFS and iterative deepening.
2. Compare memory usage and completeness with BFS and DFS.
3. Apply DFID to example search trees.

Software Required
- Python 3.8+
- Jupyter Notebook / VS Code
- Libraries: numpy, matplotlib

Theory
Iterative deepening combines depth-first search's space efficiency with breadth-first search's completeness by repeatedly executing depth-limited searches with increasing depth limits until the goal is found.

Algorithm (pseudocode)
Iterative Deepening (DFID)
1. procedure IDDFS(start, goal)
2.    for depth = 0 to max_depth:
3.        if DLS(start, goal, depth) == success: return path
4.    return failure

DLS(node, goal, depth)
1. if depth == 0 and node == goal: return success
2. if depth > 0:
3.    for each neighbor in neighbors(node):
4.        if DLS(neighbor, goal, depth-1) == success: return success
5. return failure

Flowchart
[Flowchart placeholder]

Code Page
[Reserved blank page for code]

Conclusion
DFID is useful for large or infinite search spaces where memory is constrained and where the depth of the solution is unknown.

CAPT Evaluation Table
(As previous practicals)

---

# Practical 4: Predicting House Prices by Linear Regression

Aim
To implement linear regression for predicting house prices using standard datasets and evaluate model performance using MSE, R-squared and residual analysis.

Objectives
1. Understand simple and multiple linear regression.
2. Implement regression with closed-form solution and with gradient descent.
3. Evaluate model using standard statistical metrics and visualizations.

Software Required
- Python 3.8+
- Jupyter Notebook / VS Code
- Libraries: numpy, pandas, scikit-learn, matplotlib, seaborn

Theory
Linear regression models the relationship between scalar dependent variable y and one or more explanatory variables X. Ordinary Least Squares (OLS) minimizes the sum of squared residuals to determine model coefficients.

Algorithm (pseudocode)
Closed-form (Normal Equation)
1. procedure FitLinearRegression(X, y)
2.    Add bias column to X
3.    theta = (X^T X)^{-1} X^T y
4.    return theta

Gradient Descent
1. initialize theta randomly
2. for iter in 1..N:
3.    gradient = (1/m) * X^T (X theta - y)
4.    theta = theta - alpha * gradient
5. return theta

Flowchart
[Flowchart placeholder]

Code Page
[Reserved blank page for code]

Conclusion
Students will build regression models, interpret coefficients, and evaluate predictive performance. They will understand biases, variance, and diagnostics for model selection.

CAPT Evaluation Table
(As previous practicals)

---

# Practical 5: K-Nearest Neighbour (KNN) Classification of Iris Dataset

Aim
To implement KNN classification and perform exploratory data analysis and model evaluation on the Iris dataset.

Objectives
1. Understand instance-based learning and distance metrics.
2. Implement KNN and tune hyperparameter K using cross-validation.
3. Evaluate classification performance using confusion matrix and accuracy/F1 metrics.

Software Required
- Python 3.8+
- scikit-learn, pandas, numpy, matplotlib, seaborn

Theory
KNN classifies an input by majority vote among its k nearest neighbors in feature space. Choice of distance metric and K affects bias-variance tradeoff.

Algorithm (pseudocode)
1. procedure KNN_Train(X_train, y_train)
2.    store training set
3. procedure KNN_Predict(x_test, k)
4.    compute distances from x_test to all X_train
5.    select k nearest points and vote majority label
6.    return predicted label

Flowchart
[Flowchart placeholder]

Code Page
[Reserved blank page for code]

Conclusion
Students will gain hands-on experience with instance-based learning, hyperparameter selection, and practical model evaluation.

CAPT Evaluation Table
(As previous practicals)

---

# Practical 6: Build Decision Trees and Random Forests

Aim
To build decision tree classifiers and ensemble them into random forests; analyze feature importance and overfitting.

Objectives
1. Implement decision trees (ID3/CART concepts).
2. Train random forests and analyze OOB error and feature importances.
3. Use pruning and regularization techniques to avoid overfitting.

Software Required
- Python 3.8+
- scikit-learn, pandas, numpy, matplotlib

Theory
Decision trees partition the input space via recursive partitioning using metrics like information gain (entropy) or Gini impurity. Random forests build multiple trees on bootstrapped samples and aggregate their predictions to reduce variance.

Algorithm (pseudocode)
Decision Tree (high-level)
1. procedure BuildTree(dataset, features)
2.    if stopping_condition(dataset): return leaf with majority label
3.    best_feature = argmax_information_gain(features)
4.    for each value in best_feature:
5.        child = BuildTree(subset, features - best_feature)
6.    return node

Random Forest
1. procedure RandomForest_Train(X, y, num_trees)
2.    for i in 1..num_trees:
3.        bootstrap_sample = sample_with_replacement(X,y)
4.        tree = BuildTree(bootstrap_sample, random_subset(features))
5.        add tree to ensemble
6.    return ensemble

Flowchart
[Flowchart placeholder]

Code Page
[Reserved blank page for code]

Conclusion
Students will understand tree-based models and ensemble methods, interpret feature importances, and apply techniques to mitigate overfitting.

CAPT Evaluation Table
(As previous practicals)

---

# Practical 7: Implement Naïve Bayes Models

Aim
To implement Naïve Bayes classifiers for categorical and continuous data and evaluate their performance on suitable datasets.

Objectives
1. Understand Bayes theorem and conditional independence assumptions.
2. Implement Gaussian Naïve Bayes and Multinomial Naïve Bayes variants.
3. Evaluate classification using precision, recall, and F1 score.

Software Required
- Python 3.8+
- scikit-learn, pandas, numpy

Theory
Naïve Bayes classifiers assume feature independence conditional on class label. Despite this simplification, they often perform well for text classification and other problems.

Algorithm (pseudocode)
1. procedure TrainNaiveBayes(X, y)
2.    compute prior probabilities P(y)
3.    compute likelihood parameters per class (mean/var for Gaussian, term probabilities for Multinomial)
4. procedure Predict(x)
5.    compute posterior P(y|x) ∝ P(y) ∏ P(x_i|y)
6.    return argmax_y posterior

Flowchart
[Flowchart placeholder]

Code Page
[Reserved blank page for code]

Conclusion
Students will learn probabilistic classification and gain practical experience implementing Naïve Bayes methods.

CAPT Evaluation Table
(As previous practicals)

---

# Practical 8: K-Means Clustering

Aim
To perform unsupervised clustering using K-means and analyze cluster validity using silhouette score and elbow method.

Objectives
1. Implement K-means algorithm from scratch.
2. Apply K-means to datasets and determine optimal K.
3. Visualize clusters and evaluate cluster quality.

Software Required
- Python 3.8+
- scikit-learn, pandas, numpy, matplotlib, seaborn

Theory
K-means partitions data into k clusters by minimizing within-cluster variance. The algorithm alternates between assigning points to nearest centroids and updating centroid positions.

Algorithm (pseudocode)
1. procedure KMeans(X, k, max_iter)
2.    initialize k centroids randomly
3.    for iter in 1..max_iter:
4.        assign each point to nearest centroid
5.        recompute centroids as mean of assigned points
6.        if centroids converge: break
7.    return centroids, assignments

Flowchart
[Flowchart placeholder]

Code Page
[Reserved blank page for code]

Conclusion
Students will understand unsupervised learning with clustering techniques and tools to choose cluster numbers and assess quality.

CAPT Evaluation Table
(As previous practicals)

---

# Practical 9: Implementing Ensembling Techniques

Aim
To study and implement ensemble learning techniques such as bagging, boosting (AdaBoost, Gradient Boosting) and stacking, and compare their performance.

Objectives
1. Understand the principles of bagging and boosting.
2. Implement AdaBoost and Gradient Boosting using scikit-learn.
3. Investigate stacking and meta-learners for combining diverse models.

Software Required
- Python 3.8+
- scikit-learn, xgboost (optional), lightgbm (optional), pandas, numpy

Theory
Ensemble methods combine multiple base learners to improve predictive performance. Boosting focuses on sequentially improving weak learners; bagging reduces variance by averaging multiple learners trained on bootstrap samples.

Algorithm (pseudocode)
AdaBoost (simplified)
1. initialize weights w_i = 1/N
2. for t in 1..T:
3.    train weak learner h_t on weighted data
4.    compute error rate ε_t
5.    compute alpha_t = 0.5 * ln((1-ε_t)/ε_t)
6.    update weights: increase weight for misclassified examples
7. final prediction = sign(sum alpha_t * h_t(x))

Flowchart
[Flowchart placeholder]

Code Page
[Reserved blank page for code]

Conclusion
Students will learn how ensembles improve robustness and accuracy and how to implement and tune popular ensemble algorithms.

CAPT Evaluation Table
(As previous practicals)

---

# Practical 10: Build SVM Models

Aim
To implement Support Vector Machines for classification and regression, explore kernel methods, and tune SVM hyperparameters.

Objectives
1. Understand margin maximization and support vectors.
2. Train linear and kernel SVMs using scikit-learn.
3. Perform hyperparameter tuning (C, gamma) and evaluate performance.

Software Required
- Python 3.8+
- scikit-learn, pandas, numpy, matplotlib

Theory
SVMs find a hyperplane that maximizes margin between classes. Kernel functions allow SVMs to operate in high-dimensional feature spaces implicitly.

Algorithm (high-level pseudocode)
1. procedure TrainSVM(X, y, kernel)
2.    solve quadratic optimization for weight vector w and bias b subject to constraints
3.    return model

Flowchart
[Flowchart placeholder]

Code Page
[Reserved blank page for code]

Conclusion
Students will gain practical experience training SVMs and understanding kernel selection and regularization trade-offs.

CAPT Evaluation Table
(As previous practicals)

---

# Grading & Rubric
A common CAPT evaluation table is used across all practicals (see earlier table). Detailed rubric for marking code, reports, and viva is provided below.

## Sample Rubric (detailed)
1. Aim & Objectives (5 marks): Clear articulation and understanding.
2. Algorithm & Flowchart (10 marks): Correctness and clarity of pseudocode/flowchart.
3. Program Implementation (25 marks): Code completeness, correctness, style, and documentation.
4. Output & Analysis (15 marks): Correct results, appropriate visualizations, and proper interpretation.
5. Report & Viva (10 marks): Well-written report and oral understanding.

---

# Appendices

## Appendix A: Sample Datasets & Download Links
- Iris dataset: https://archive.ics.uci.edu/ml/datasets/iris
- Boston house prices (or alternative): note that Boston dataset has ethical concerns and may be deprecated; use Kaggle or other public datasets for house prices.
- Sample CSV links and instructions will be included in the DOCX/PDF deliverable.

## Appendix B: Suggested Reading & References
1. Stuart Russell and Peter Norvig, "Artificial Intelligence: A Modern Approach".
2. Hastie, Tibshirani, Friedman, "The Elements of Statistical Learning".
3. Géron, "Hands-On Machine Learning with Scikit-Learn, Keras, and TensorFlow".
4. Scikit-learn documentation: https://scikit-learn.org

## Appendix C: Lab Safety and Policy
- Maintain academic integrity while using datasets and code.
- Follow lab usage timings and backup your work.

---

# Notes on formatting and conversion
This markdown file contains the complete manual content structured for conversion to Word (.docx) or PDF. When converted to Word:
- Use Times New Roman, 12 pt for body text.
- Heading styles should match the sample manual (Heading 1 for practical titles, Heading 2 for subheadings).
- Insert the provided logo image in the header and apply a light-blue rectangle background on the cover page.
- For each "Flowchart placeholder" insert a clean vector flowchart diagram; for code pages, insert a full page with ~40 blank lines.

---

End of manual (Markdown version)
