# Covid-19-GNN
## Dependencies
[![PyPI pyversions](https://img.shields.io/pypi/pyversions/ansicolortags.svg)](https://pypi.python.org/pypi/ansicolortags/)
```
pip install numpy, pandas, seaborn, matplotlib, dgl, networkx, torch, sklearn, scipy
```
## Abstract
Using [Italy government data](https://github.com/pcm-dpc/COVID-19 "Data Source"), we created a Graph Neural Network model that utilize the values from SIR model as the baseline values. The performance of the final GNN achieved mean squared log error of 3.60 which outperforms all other models.
## Sections
### SIR and variants
SIR model has been the go-to-model for infectious disease studies, we used `scipy` to solve the differential equations.
Moreover, we investigated the variants, SEIR (E for Exposed) and SIRD (D for Deceased).
It is worth mentioning that SIR model and its varients are not suitable for multiple peaks pandemic which is our case. Therefore, we split up the data into 2 sections to improve the models' performance.
### Neural Network
We decided to use neural network as it was shown in the last decade to be very powerful when it comes to prediction. We chose to explored both wide neural network and deep neural network.
At the end, we confirmed with mainstream belief of deep neural network outperformning wide neual network.
### GNN
Since pandemic has a geophraical nature, we tried to incorporate this property into our network. Using `networkx` and `dgl`, we used the distance between each province as the edge weight which can reflect the fact that provinces that are further away are harder to reach. 

<img src="https://github.com/fancent/Covid-19-GNN/blob/main/img/graph_structure.png" alt="graph structure" width="49%" border="5" />

Then, we used similar structure as the model used in [How Powerful are Graph Neural Networks?](https://arxiv.org/pdf/1810.00826.pdf).
Finally, we stacked our SIR model's prediction with the GNN to create a even better model.
### Results
<img src="https://github.com/fancent/Covid-19-GNN/blob/main/img/graph_1.png" alt="result graph 1" width="49%" border="5" /><img src="https://github.com/fancent/Covid-19-GNN/blob/main/img/graph_2.png" alt="result graph 2" width="49%" border="5" />
Above graphs are the mean squared log error of each model by provinces. The rankings of each model are as follow:
1. SIR Deep GNN
2. Deep GNN
3. Wide GNN
4. Deep NN
5. Wide NN
