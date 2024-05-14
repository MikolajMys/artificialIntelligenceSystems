```python
import numpy as np
from collections import Counter

class Node:
    def __init__(self, feature=None, threshold=None, left=None, right=None,*,value=None):
        self.feature = feature
        self.threshold = threshold
        self.left = left
        self.right = right
        self.value = value
        
    def is_leaf_node(self):
        return self.value is not None

class DecisionTree:
    def __init__(self, min_samples_split=2, max_depth=100, n_features=None):
        self.min_samples_split = min_samples_split
        self.max_depth = max_depth
        self.n_features=n_features
        self.root=None

    def fit(self):
        
    def _grow_tree(self):
        
    def _best_split(self):
        
    def _best_split(self):
        
    def _information_gain(self):
        
    def _split(self):
        
    def _entropy(self):
        
    def _traverse_tree(self):
        
    def predict(self):
```
