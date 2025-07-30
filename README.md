# pay-equity-2
This is an R Shiny application to display the extent of gender pay disparity among federal employees by GS (General Schedule) level.

### The Data
The data come from the FedScope current month dataset which can be accessed here:
https://www.fedscope.opm.gov/ibmcognos/bi/v1/disp?b_action=powerPlayService&m_encoding=UTF-8&BZ=1AAABnsT72MN42oVOsW6DQAz9mTNph0Y_wyVhYIDjUBiANLBXlFzSqsBFcB3y9xUwpFWGvidL9vN7lp2yWJdVcVRpHIzWDDqNn4DocyNI4jZU6PncQ0%7EtfIHRZiO5UKREtAWiZ2fKqvAo94ew2gdASWN6q3sLlJxNe9IDiAg87OtOgxuvDnXzVV%7E0_Ka6a2tune7tCkQMlFyXzV%7E73QWEL0Aov4dhmTLT248p68SlXMsiz5Ws0iLPw0wF%7E_Wc6DU4IzKOiJwjYwyZQEbIJjIWXnTf3IAQ6ASEYdsC_pkZ7eMpQJ8B7YBcBNIc6B3IXwR_F9gMIHey%7EwKfOXfLO3MtTyz4AbZLbJc%3D

I created and downloaded a crosstab of data, where rows were defined by GS level and gender, and columns were defined by pay level.  Note that raw pay is not provided in these data; instead employees are grouped into pay categories (Less than $20,000, $20,000 - 29,999, $30,000 - 39,999, etc.).  

#### Pay categories
Note that pay category width is not constant:
1. The lowest category (< $20,000) is less than $5K wide (based on a federal minimum wage of $15,080).
1. Between $20,000 and $199,999, pay categories are $10K wide.
1. Between $200,000 and $299,999, pay categories are $20K wide.
1. Between $300,000 and $499,999, pay categories are $50K wide.
1. Width of the highest category ($500,000+) is unknown.

### global.R
This program does initial loading of required libraries, plus data preprocessing.

#### Ladder analysis
This application will use a method of pay equity analysis I developed which I call __ladder analysis__.  Ladder analysis compares the proportion of focal group members at each pay level to the proportion of focal group members at the specific GS level.  An overall laddder analysis can also be conducted.  The advantage of ladder analysis is that a statistical test (specifically, the single-sample z-test) can be used to estimate whether the proportion of focal group at a pay level is statistically significantly lower than would be expected based on the proportion of focal group employees at the GS level.

Obviously, ladder analysis is inferior to a multivariate analysis of individual-level pay data.  But it may be suggestive of potential problem areas.

### ui.R
This program contains the user interface.

### server.R
This program contains the server logic.

### Analytical logic
Because we only have count data
