# Neural Network for Drug Discovery.

 ## Results
<p align="center">
    <img height="300px" src="Screenshot 2022-10-10 at 10.15.49 PM.png" width="350px"/>
    
<img height="300" src="Screenshot 2022-10-10 at 10.26.54 PM.png" width="350"/>  
</p>

 ## Analysis

Neural networks worked promisingly in this task and outperformed accuracy of decision
trees by a whopping `13%`. 

<h3>Regularization</h3>

The majority of effort went `into choosing the best size neural network` with respective `regularization` hypermeter. 
As soon as I started training **without regularization** the NN started **overfitting** the data starting from _2nd iteration_. After some research it was apparent to use regularization parameters. I had 3 options: `L1, L2 regularization and Dropout` method. L1 and L2 penalizes weights while drop out omits certain neurons. `L1 could make a weight 0` while `L2 is extremely slow` in pushing weight `towards 0`. I did not use the feature subset. In other words, I wanted the `NN to decide which feature to omit/reduce` effect on by using loss fucntion and backpropagation. As I wanted the weights to be 0 for irrelevant features so, I used `L1 regularization`.

Choosing the right for L1 regularization was another challenging task. To come up with a value It tried 𝝺
`bigger values first`. They did **not let the model fit** to the data. Then I tried smaller values which **led to overfitting**. Sort of **like binary search** I used intermediate values to come up with the value that worked

<h3>Loss Function</h3>
Initially, I used `Binary Cross Entropy` as the loss function but the issue was it was not able to produce good results. 
`As it does not take imbalance into account`. Also, gradient descent updates the weight for prediction towards the confident class. Because, the majority class dominates the loss function. `Binary Focal Cross Entropy` however, was a better choice because it weights class prediction and forces the model to learn parameters towards the hard to classify class. The following is the distinction between model F1-Score during training and testing using Binary Cross Entropy on the Right and Binary Focal Cross Entropy on the Left. As it is clear that Focal Cross Entropy converges a lot better than the counterpart Binary cross entropy.!

# Decision Trees


<p align="center">
<img height="350" src="Screenshot 2022-10-10 at 2.39.58 PM.png" width="350px"/>
<img height="350" src="Screenshot 2022-10-10 at 2.40.52 PM.png" width="350"/>
</p>


### Analysis

As the data is less, the decision tree started to **overfit on the training** data as soon as I started
training it. Which performed very badly on the testing data set. To avoid overfitting I tried 2 different methods. `Pre-pruning and Post-pruning`. Pre-pruning however, was not able to produce good results. As it is **hard to understand** optimal **depth** of the tree and **minimum records** to split at any level by just looking at the data.

I found **Post-pruning** promising as it prunes the tree and then determines the accuracy and further prunes it. I was able to get a boost of 5% in the F1-Score after using post pruning in miner2. I used cost-complexity-pruning method. In this method we assign a score to every tree. The score is defined as `Tree Score = Misclassification + ɑ * (Number of terminal nodes )`. 

The idea is to reduce the number of leaves and miss classification error while increasing the alpha. Finally the tree alpha where the tree has higher training and testing accuracy will be chosen.


