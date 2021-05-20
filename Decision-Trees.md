# **Understanding Decision Trees**

## **What is a Decision Tree?**

Decision Tree is our goto algorithm when we start solving either a **Classification** or a **Regression** problem. Tree based algorithm are used widely mostly because of their simplicity and they are easy to visualize. 

A Decision Tree has 3 main elements:

1. A Decision Tree is drawn upside down with the _Root Node_ on the top
2. _Internal Nodes_ are the ones based on which the tree split into branches
3. Finally the end of a branch which dos not split is called a _Leaf Node_

<img src="https://github.com/amit-raj-repo/Machine-Learning/blob/main/Tree%20Elements.png?raw=true" width="600" height ="400">

To get a better understanding of Decision Trees, imagine you are in a bookshop and are contemplating which book to buy. A simple Decision Tree will help you make your decision.

<img src="https://github.com/amit-raj-repo/Machine-Learning/blob/main/Tree%20Example.png?raw=true" width="550" height ="400">

After understanding the basic terminologies, lets look into how a Decision Tree Algorithm works!


## **Decision Tree - Algorithm**

### ***Problem Context***

Suppose you are solving a _Classification Problem_ where you need to predict if a person can solve a puzzle or not. There are 3 independent variables at you disposal

**Age -** This is a continuous variable with values between 15 to 60 years

**Gender -** A Binary variable with values as Male and Female

**Nationality -** A Multi-Level variable with values like Indian, German, Chinese etc. a total of 15 different Nationalities

We are trying to predict if a person is able to solve a puzzle or not, which means our dependent variable takes values as 

- _1_ If a person can solve the puzzle
- _0_ Otherwise

But before we jump into how trees are made, let's look at **Gini Index** 

### ***Gini Index***

**Gini Index** is the criteria used by the tree to decide _which variable to split by_ and by _what value_. **Gini Index** is calculated based on the following formula

<img src="https://github.com/amit-raj-repo/Machine-Learning/blob/main/Gini%20Impurity.png?raw=true" width="200" height ="75">

Where,
**C** = Number of Classes (In the current case it's 2, can be _n_)

For creating a **Decision Tree**, we need to find the best split at every point starting from the _root node_. To ensure that we need to select a _variable & value_ where the **Gini Impurity is Minimum**

### ***Algorithm***

- Given our use case, we have _3 Independent Variables_, we start by finding the one which gives us the best split i.e. **Minimum Gini Impurity**
  - We start with *Gender* and calculate the overall _Gini Impurity_ for the variable
  
  <img src="https://github.com/amit-raj-repo/Machine-Learning/blob/main/SmartSelect_20210519-114845_Samsung%20Notes.jpg?raw=true" width="600" height ="300">

  <img src="https://github.com/amit-raj-repo/Machine-Learning/blob/main/SmartSelect_20210519-114922_Samsung%20Notes.jpg?raw=true" width="600" height ="800">

- Similarly **Gini Impurity** will be calculated for Nationalities as well, for Nationalities we will have split as _Indian or Not_ or _German or Not_
  
- Next we'll tackle a continuous variable and calculate _Gini Impurity_. To calculate _Gini Impurity_ for Age, we'll follow the following steps:
  - Arrange the column values in ***Ascending Order***
  - For every ***Adjacent Entry*** calculate the *Average* i.e. say the first Age entry is 30 and the next one is 40, our splitting value will be 35 which is the _Average of 30 and 40_
    
      <img src="https://github.com/amit-raj-repo/Machine-Learning/blob/main/SmartSelect_20210519-114959_Samsung%20Notes.jpg?raw=true" width="600" height ="200">
      <img src="https://github.com/amit-raj-repo/Machine-Learning/blob/main/SmartSelect_20210519-115043_Samsung%20Notes.jpg?raw=true" width="600" height ="700">

  - We need to repeat the above 2 steps for all _Adjacent Entries_
  - Out of all the ***Gini Impurities*** for _Age_, choose the one with minimum impurities
  - Say we get minimum Impurity value for _Age = 50_ i.e. 0.38

- After Calculating ***Gini Impurities*** for all the variables we get the following results:
  - **Gender - Male** = 0.35
  - **Nationality - Indian** = 0.45
  - **Age - 50** = 0.38

From the results, we can can conclude that **Gender - Male** is our best choice for ***Root Node***

We will carry out the same steps and grow the tree further until a stopping criteria is reached.

## ***Advantages of Decision Trees***

1. Decision Trees are Simple to understand, interpret, visualize
2. Decision trees implicitly perform variable or feature selection
3. Can handle both numerical and categorical data
4. Can also handle multi-output problems
5. Nonlinear relationships between parameters do not affect tree performance

After going through this post, you'll have a fair idea of how Decision Tree work for a ***Classification Problem***. 

Posts you might be interested in:

- **Regression Trees**
- **Decision Tree Implementation & Hyperparameter Tuning**
