## Neural Network for Drug Discovery.

 ### Results
<p align="center">
    <img height="300px" src="Screenshot 2022-10-10 at 10.15.49 PM.png" width="350px"/>
    
<img height="300" src="Screenshot 2022-10-10 at 10.26.54 PM.png" width="350"/>  
</p>

 ### Analysis

Neural networks worked promisingly in this task and outperformed accuracy of decision
trees by a whopping `13%`. 

The majority of effort went `into choosing the best size neural network` with respective `regularization` hypermeter. 
As soon as I started training **without regularization** the NN started **overfitting** the data starting from _2nd iteration_. After some research it was apparent to use regularization parameters. I had 3 options: `L1, L2 regularization and Dropout` method. L1 and L2 penalizes weights while drop out omits certain neurons. `L1 could make a weight 0` while `L2 is extremely slow` in pushing weight `towards 0`. I did not use the feature subset. In other words, I wanted the `NN to decide which feature to omit/reduce` effect on by using loss fucntion and backpropagation. As I wanted the weights to be 0 for irrelevant features so, I used `L1 regularization`.

Choosing the right for L1 regularization was another challenging task. To come up with a value It tried 𝝺
`bigger values first`. They did **not let the model fit** to the data. Then I tried smaller values which **led to overfitting**. Sort of **like binary search** I used intermediate values to come up with the value that worked

Initially, I used `Binary Cross Entropy` as the loss function but the issue was it was not able to produce good results. 
`As it does not take imbalance into account`. Also, gradient descent updates the weight for prediction towards the confident class. Because, the majority class dominates the loss function. `Binary Focal Cross Entropy` however, was a better choice because it weights class prediction and forces the model to learn parameters towards the hard to classify class. The following is the distinction between model F1-Score during training and testing using Binary Cross Entropy on the Right and Binary Focal Cross Entropy on the Left. As it is clear that Focal Cross Entropy converges a lot better than the counterpart Binary cross entropy.!

