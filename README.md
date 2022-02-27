# titanic-eda
<h1>Titanic exploratory data analysis</h1>
        <a target = '_blank' href="https://github.com/dduygaucho/titanic-eda">View the complete project on Github</a>
        <p>This notebook aims at 2 goals: analyzing the titanic dataset to find out the underlying assumptions and predicting whether a person would have survived or not given their information</p>
        <p>Steps</p>
        <ol>
            <li><a href="#data">Data wrangling</a></li> 
            <li><a href="#feature-engineering">Data analysis</a></li>
            <li><a href="#exploration">Machine learning</a></li>

        </ol>

        <h2 id = 'data'>Data wrangling</h2>
        <h3>Data summary</h3>
        <p>A summary of the dataset shows that the dataset is mostly clean, except the 2 features which are Age and Cabin</p>
        <h3>Data cleaning</h3>
        <p>The feature cabin has so many missing values so it won't add up too much value to our analysis. In addition, as the ticket is unique to each person, which might depend on other values, so it is removed too. </p>
        <p> The PassengerId feature should also be removed as it is basically the index</p>
        <p> However, the age feature should be imputed with the mean value by using the Simple Imputer later</p>


        <h2 id = 'feature-engineering'>Data analysis</h2>
        <h3>Data Visualization</h3>

  

        <a target = '_blank' href="https://github.com/dduygaucho/titanic-eda">More about the conclusion can be found in the Notebook</a>

        <h3>Group analysis</h3>

        <p>Almost nothing useful. Potentially interesting: </p>
        <ol>
        <li>1st class have higher survival rate (First label)</li>
        <li>3rd class was travelling in larger families (Third label) </li>
        <li>2nd and 3rd class fare was very close
        larger families had more children (low age passengers) in them </li>
        </ol>



        <p>In general for all classes: </p>

            <li>In every age group, women were more likely to be saved
            among children, this difference is minimal</li>
            <li>On average, children are more likely to be saved than adults
            young men (15-25 years old) and old men survived least of all (although there are not enough statistics there)</li>
            <li>Most of all women aged over 50 survived</li>
            Analysis by class:

            <li>In classes 1 and 2, the vast majority of women were saved</li>
            <li>In classes 1 and 2 there were very few children and a quite a lot of old people</li>
            <li>There were very few people over 50 in class 3
            in the 2nd and 3rd classes, very few men were saved</li>


        

        <h2 id = 'feature-engineering'>EDA results</h2>

            
        <p>Lets sum up our discoveries concerning importance of given features: </p>

        <li>PassengerId - useless  </li>
        <li>Pclass - super useful. Shoud be categorical, not numerical or even ranged in my opinion </li>
        <li>Name - full name including some titles. There is lots of information there, but it doesn't seem to have any predictive power </li>
        <li>Sex - super useful (pun intended) </li>
        <li>Age - useful, especially for children (higher survival rate). Problem: lots of missing values! Probably should be converted into categories like: child, adult, unknown </li>
        <li>SibSp + Parch - somewhat useful, not explicit. Maybe shoud be aggregated into one feature 'family_size' </li>
        <li>Ticket - seems to be useless </li>
        <li>Fare - maybe useful, maybe not. Should be tested </li>
        <li>Cabin - lots of missimg values. Consists of deck (letter) and room number. Room number is useless, deck letter probably can be useful </li>
        <li>Embarked - maybe useful, maybe not. Should be tested. There are a few missing values, can be safely filled with most popular value </li>

		<h2 id = 'exploration'>Machine learning</h2>
        <p>In this case, 3 algorithms, including logistic classifier, support vector machine, random forest are applied to find the best model for prediction of survival. In addition, a neural network is also used as a reference to prove whether it is always best to use deep learning or not.  </p>
        <p>In general, random forest outperforms the other 2 algorithms with an accuracy of 97.98% on the training set and 100% on the test set (More information about the accuracy of other algorithms can be found <a target = '_blank' href = "https://github.com/dduygaucho/titanic-eda">here</a></p>
        <p>However, neural networks are unlikely to work well in this situation, it soonly becomes overfit although the hyperparameters have been fine-tuned and the learning rate is quite small.</p>
        
