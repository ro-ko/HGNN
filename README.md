# HGNN
This repository aims to reproduce **HGCN** proposed in the paper entitled "Hypergraph Neural Networks (AAAI'2019)". 
 We refer to [the original repository](https://github.com/iMoonLab/HGNN) of **HGNN** to implement this repository. 

## Dependencies
 We use the following Python packages to implement this. Install them in your environment using `pip install -r requirements.txt`. 

 * tqdm == 4.63.0  
 * torch == 1.4.0  
 * scipy == 1.5.2  
 * numpy == 1.19.2  

## Training
To train and evaluate the model, type the following command: 
 ```bash
python train.py
 ```

 It will train the model for the node classification task in the given hypergraph. 

 In this project, you can control the value of each hyperparameter in `config.yaml`. 
 The details of the hyperparameters are in the following table.

 Option | Description | Default
 ------- | ---------- | --------
 on_dataset | cora, pubmed, modelnet40, NTU | modelnet40
 K_neigs | assignmetn to bulid hyperedge in modelnet40, NTU dataset | 10
 n_hid | feature numbers of hidden layer | 128
 dropout | dropout probability for hidden layers | 0.5
 max_epoch | number of training epochs | 600
 lr | learning rate | 0.001
 decay_rate | weight decay | 0.0005
 decay_step | weight decay step | 200
 gamma | gamma | 0.9

 ## Experimental setting

 ### Datasets
 We use the following datasets for the experiments. 
 * coauthorship : dblp, cora  
 * cocitation : citeseer, cora, pubmed
 * visual object : MVCNN feature, GVCNN featrue

 ### Default Hyperparameters
 The followings are default hyperparameters, as described in **[the original repository](https://github.com/malllabiisc/HyperGCN)**. 
 * hidden nodes size per layer : 128  
 * dropout rate : 0.5  
 * learning rate : 0.001  
 * decay rate : 0.0005  
 * decay step : 200  
 * training epochs : 600  


## How to construct hypergraph from graph dataset CORA, Pumbed

The originaly repository does not support hypergraph dataset CORA, Pumbed. The way to produce the hypergraph dataset for its paper experiment(the related issue is found [here](https://github.com/iMoonLab/HGNN/issues/3)).  
Becareful NaN or Inf problem during processing(the related issue is found [here](https://github.com/iMoonLab/HGNN/issues/14))  
Or download dataset from [here](https://github.com/ro-ko/HyperGCN-pytorch).

### The experimental result of the paper

 | Dataset | Pubmed | Cora 
 ------- | ------ | ---- 
 HGNN | 80.1% | 81.6% 


- Dataset : ModelNet40 

 | Features for structure | Visual object <br> MVCNN feature+GVCNN featrue | Visual object <br> MVCNN feature | Visual object <br> GVCNN featrue
 ------- | ------ | ---- | ---- 
 GVCNN | 92.6% | 91.8% | 96.6% 
 MVCNN | 92.5% | 91.0% | 96.6%
 GVCNN+MVCNN | - | - | 96.7% 

- Dataset : NTU

 | Features for structure | Visual object <br> MVCNN feature+GVCNN featrue | Visual object <br> MVCNN feature | Visual object <br> GVCNN featrue
 ------- | ------ | ---- | ---- 
 GVCNN | 82.5% | 79.1% | 84.2% 
 MVCNN | 77.2% | 75.6% | 83.6%
 GVCNN+MVCNN | - | - | 84.2% 
 
### The reproduced result

 | Dataset | Pubmed | Cora 
 ------- | ------ | ---- 
 HGNN | - | - 


- Dataset : ModelNet40 

 | Features for structure | Visual object <br> MVCNN feature+GVCNN featrue | Visual object <br> MVCNN feature | Visual object <br> GVCNN featrue
 ------- | ------ | ---- | ---- 
 GVCNN | - | - | - 
 MVCNN | - | - | -
 GVCNN+MVCNN | - | - | - 

- Dataset : NTU

 | Features for structure | Visual object <br> MVCNN feature+GVCNN featrue | Visual object <br> MVCNN feature | Visual object <br> GVCNN featrue
 ------- | ------ | ---- | ---- 
 GVCNN | - | - | - 
 MVCNN | - | - | -
 GVCNN+MVCNN | - | - | - 


### Hyperparameter tuning

We think that the problematic hyperparameters are `-` and `-`. 
To find better hyperparameters, we perform grid searches for `-` and `-` as follows:
- [-] = [-]  
- [-] = [-]  

We summarize the result of this experiment in the following table. 
We report the average of test errors (lower is better) with their standard deviation over 10 runs (accuracy = 100 - error). 

  Task | Method | Learning rate | Epochs | Error ± std
 ----- | ------ | ------ | ------- | -------

 
 ## References
 [1] Feng, Y., You, H., Zhang, Z., Ji, R., & Gao, Y. (2019). Hypergraph Neural Networks. Proceedings of the AAAI Conference on Artificial Intelligence, 33(01), 3558-3565. 