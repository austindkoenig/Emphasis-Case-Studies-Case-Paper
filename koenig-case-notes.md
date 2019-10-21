# <center>Predicting Customer Churn at QWE Inc.:<br>Preliminary Case Notes</center>

<center>Austin Koenig</center>
<center><i>Emphasis Case Studies</i></center>

## Case Summary

Richard Wall, VP of customer services at QWE Inc., had asked V. J. Aggrawal to take up a project which predicts the probability of customer churn. Here, customer churn is defined as whether or not the customer unsubscribes from QWE's service in the following number of months (in this case, they are predicting two months ahead). Since the data available to Aggrawal was rather vast and complicated, he went back to Wall for consultation. Being asked where to first look, Wall pointed his associate to the following features:

- **Customer Age** : the number of months a customer has been a subscriber of the service
- **Customer Happiness Index (CHI)** : a conglomerate score related to customer experience with the service
- **Service and Usage Patterns** : several features describing how the customer uses the service

Aggrawal then obtained a sample accounting for these features.

## Possible Alternative Features

For this case, the obvious thing to do is consider more features which Aggrawal could have used or engineered. This section describes alternative features in depth. Let's consider how the diversity of customers affects customer churn.

**Supposition A**: The corporate characteristics of subscribers has a general affect on churn.

While Wall and Aggrawal worked within their means, they only picked data that referred to the relationship between subscribers and QWE. This is no fault of theirs as an exploratory experiment within the QWE SalesForce database may not have the time to initially explore depth along with breadth. Hence, taking into account the individual characteristics of their longest-standing and shortest-standing subscribers might build a useful profile in the improved prediction of customer churn. This would help to answer the question of what kind of companies unsubscribe or remain subscribed.

**Supposition A** leads to the idea of a company profile with which to organize the customers of QWE. This profile should account for the following:

- Character and behavior of company
- External company performance
- Internal company performance

Each of these categories encapsulates a feature subspace within the space of possible features. However, since much of the data within these subspaces are probably not publicly available, we can employ submodels to approximate these prohibited features for companies based on publicly available data. By including the features in the study, we can create a company profile encoding with which to describe each of the QWE customers. Then, we can use this encoding as a set of features in the model which predicts churn.

Let's go deeper into these subspaces and define some of the features we can use to describe a company as well as some potential sources of or ways to generate these data:

| Category | Desired Feature | Potential Data Source |
| --- | --- | --- |
| Character/Behavior | Public Opinion*<br>Peer/Management Reviews*<br>Philanthropic Relations<br>Legal Behavior*<br>Customer Reviews* | NLP Sentiment Analysis of Top News Sources<br>NLP Sentiment Analysis of Employee Reviews<br>Finance Database Query<br>HR Database Query<br>NLP Sentiment Analysis of Customer Reviews |
| External Performance | Periodic Reported Metrics<br>Customer Reviews*<br>Dollar Value of Public Associations | Quarterly/Yearly Reports Query<br>NLP Sentiment Analysis of Customer Reviews<br>Finance Database Query |
| Internal Performance | Peer/Management Reviews*<br>Measure of Efficiency<br>Hire/Fire/Quit Rates | NLP Sentiment Analysis of Employee Reviews<br>Operations Reports per Time Period<br>HR Database Query |

An asterisk (*) indicates that the feature may be a derived feature, meaning that there is some nondeterministic process required to produce it.

### Proposed Feature List

This section proposes the full feature list for this project.

- Given Features:
  - ID
  - Customer Age
  - Customer Happiness Index (CHI)
  - Number of Support Cases
  - Average Support Case Priority
  - Number of Logins
  - Number of Blog Articles Written
  - Number of Views
  - Number of Days Since Last Login
- Comprehensive Customer Profile:
  - Customer Character/Behavior Index (CCBI)
  - 
