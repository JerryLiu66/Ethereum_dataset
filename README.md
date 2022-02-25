# Ethereum_dataset
This file contains an ETH transaction network obtained from original Ethereum transaction records with some filtering rules, which total contains 1,402,220 nodes and 2,815,028 edges. For the dataset, we first obtain 816 ground-truth labels from an official Ethereum explorer, and then include the transaction relationships within the two-hop neighborhood of each labeled account. Next, we filter out the zero-ETH transactions and obtain a network containing most of the nodes in its largest connected component. For each node, 12 features such as transaction amount, account balance, number of transactions, and frequency of transactions are extracted. Both the adjacency matrix and the feature matrix are available.

To use the dataset, you can call the following function:
```python
def loadEtherFromNPZ(dataset_dir):
    adj = sp.load_npz(dataset_dir + "ether_adj.npz")
    data = np.load(dataset_dir + "ether_features.npz")
    np.nan_to_num(data['feats'])

    return adj, data['feats'], data['y_train'], data['y_val'], data['y_test'], data['train_index'], data['val_index'], \
           data['test_index'], data['train_target']
```
