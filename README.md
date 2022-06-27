

## Background


## Robo Advisor for Retirement Plans

![Robot](https://github.com/joannemannuella/unit13-challenge/blob/main/RoboAdvisor/Icons_Images/robot.jpg)


### Background

In this task I was hired as a digital transformation consultant by one of the most prominent retirement plan providers in the country; they want to increase their client portfolio, especially by engaging young people. Since machine learning and NLP are disrupting finance to improve customer experience, you decide to create a robo advisor that could be used by customers or potential new customers to get investment portfolio recommendations for retirement.

In this homework assignment, I am to create a bot that will recommend an investment portfolio for a retirement plan.

I accomplish the following main tasks:

1. **Initial Robo Advisor Configuration** Define an Amazon Lex bot with a single intent that establishes a conversation about the requirements to suggest an investment portfolio for retirement.

2. **Build and Test the Robo Advisor** Make sure that your bot is working and responding accurately along with the conversation with the user, by building and testing it.

3. [**Enhance the Robo Advisor with an Amazon Lambda Function**](https://github.com/joannemannuella/unit13-challenge/blob/main/RoboAdvisor/Code/lambda_function.py) Create an Amazon Lambda function that validates the user's input and returns the investment portfolio recommendation. This task includes testing the Amazon Lambda function and making the integration with the bot.

---

#### Initial Robo Advisor Configuration

In this section, I created the `RoboAdvisor` bot and add an intent with its corresponding slots.

. Use the following parameters:

* **Bot name:** RoboAdvisor
* **Output voice**: Nicole
* **Session timeout:** 5 minutes
* **Sentiment analysis:** No
* **COPPA**: No
* **Advanced options**: No
* *Leave default values for all other options.*

I Create the `RecommendPortfolio` intent, and configure some sample utterances as follows :

* I want to save money for my retirement
* I'm ​`{age}​` and I would like to invest for my retirement
* I'm `​{age}​` and I want to invest for my retirement
* I want the best option to invest for my retirement
* I'm worried about my retirement
* I want to invest for my retirement
* I would like to invest for my retirement

This bot used four slots, three using built-in types `FirstName`, `age`, `investmentAmount1` and one custom slot named `riskLevel`. 

#### Build and Test the Robo Advisor


#### Enhance the Robo Advisor with an Amazon Lambda Function

In this section, I created an Amazon Lambda function that will validate the data provided by the user on the Robo Advisor. I created a new lambda function from scratch and name it `recommendPortfolio`.  I Selected Python 3.7 as runtime.

In the Lambda function I completed [`recommend_portfolio()`](https://github.com/joannemannuella/unit13-challenge/blob/main/RoboAdvisor/Code/lambda_function.py) function by following these guidelines:

##### User Input Validation

* The `age` should be greater than zero and less than 65.
* the `investment_amount` should be equal to or greater than 5000.

##### Investment Portfolio Recommendation

Once the intent is fulfilled, the bot should response with an investment recommendation based on the selected risk level as follows:

* **none:** "100% bonds (AGG), 0% equities (SPY)"
* **very low:** "80% bonds (AGG), 20% equities (SPY)"
* **low:** "60% bonds (AGG), 40% equities (SPY)"
* **medium:** "40% bonds (AGG), 60% equities (SPY)"
* **high:** "20% bonds (AGG), 80% equities (SPY)"
* **very high:** "0% bonds (AGG), 100% equities (SPY)"

Once I finished  coding your lambda function, I  test it using the [sample test cases](https://github.com/joannemannuella/unit13-challenge/tree/main/RoboAdvisor/Test_Cases) provided for this homework.

* [age_error](https://github.com/joannemannuella/unit13-challenge/blob/main/RoboAdvisor/Test_Cases/age_error.txt)

![age](https://github.com/joannemannuella/unit13-challenge/blob/main/RoboAdvisor/Icons_Images/age_error.png)

* [incorrect_amount](https://github.com/joannemannuella/unit13-challenge/blob/main/RoboAdvisor/Test_Cases/incorrect_amount_error.txt)

![amount](https://github.com/joannemannuella/unit13-challenge/blob/main/RoboAdvisor/Icons_Images/incorrect_amount.png)

* [negative_age](https://github.com/joannemannuella/unit13-challenge/blob/main/RoboAdvisor/Test_Cases/negative_age_error.txt)

![negative_age](https://github.com/joannemannuella/unit13-challenge/blob/main/RoboAdvisor/Icons_Images/negative_age.png)

* [correct_dialog](https://github.com/joannemannuella/unit13-challenge/blob/main/RoboAdvisor/Test_Cases/correct_dialog.txt)

![correct_dialog](https://github.com/joannemannuella/unit13-challenge/blob/main/RoboAdvisor/Icons_Images/correct_dialog.png)


#### Build and Test the Robo Advisor with Lambda Function


![Robo Advisor test](https://github.com/joannemannuella/unit13-challenge/blob/main/RoboAdvisor/Demo%20Lex/Lex%20GIF.gif)

For full demo video find [here](https://github.com/joannemannuella/unit13-challenge/blob/main/RoboAdvisor/Demo%20Lex/Amazon%20Lex%20-%20Google%20Chrome%202022-06-27%2013-11-28.mp4)
