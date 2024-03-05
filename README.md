# Case-Email-Campaign-Performance-anyalsis
# Business and Tech goal
Help the client of our company which is a retail company to test their email campaign's performance, increace their customer's engagement and comapny's total sales.
Analyzing KPIs such as click rate, conversion rate, retention rate and others to seek business opptunities.
# Data model
![email campagin snow flake schema](https://github.com/ethanzzz118/Case-Email-Campaign-Performance-anyalsis/assets/110695227/85d95d7f-c129-4823-bcd3-126cddd29f9f)
# some key requirements
1.Based your understanding, please define retention rate, write a SQL query that calculates for Day 10 and Day 30 retention rate for month of September.
![c1856e9714a48ba84aeec74a80722cb](https://github.com/ethanzzz118/Case-Email-Campaign-Performance-anyalsis/assets/110695227/077790d0-89b7-43f8-8202-dc54a92efdb1)
![20fd5f78adcfedca643723cecab6b7d](https://github.com/ethanzzz118/Case-Email-Campaign-Performance-anyalsis/assets/110695227/749b80a1-e665-44a9-baa2-84e3a473cbf0)
2.What factor do you think it could impact retention rate, write a SQL query to show one of your assumptions and explain.
![17218ac35860193a5551a81822add8d](https://github.com/ethanzzz118/Case-Email-Campaign-Performance-anyalsis/assets/110695227/dd433e1f-c603-460e-b482-39c07d1cbb6d)
3.Based your understanding, please define churn rate, what data or column do we need to calculate churn rate?  Add whatever columns you need to any three tables and write a SQL query that calculates churn rate for the month of September.
Churn rate is a business metric that calculates the rate at which customers stop doing business with an entity. It is a measure of customer attrition and is generally expressed as a percentage.
churn rate would refer to the percentage of clients who have stopped making transactions over a certain period of time, often after having been previously active.
![bf539e98bfe37d02c29540556680b67](https://github.com/ethanzzz118/Case-Email-Campaign-Performance-anyalsis/assets/110695227/33552bca-af7d-4962-a864-70e8c14b3e8a)
4.Write a SQL to calculate click rate % lift for Target over Control for all the campaigns in the month of September.
![5b160e81ac154568d43675f62958a9f](https://github.com/ethanzzz118/Case-Email-Campaign-Performance-anyalsis/assets/110695227/bfa11831-e50f-44bc-89f2-28bb4ceab4e2)
![f52e3bf131de85a4310c364cbe2c18f](https://github.com/ethanzzz118/Case-Email-Campaign-Performance-anyalsis/assets/110695227/8d5beecb-8541-4b59-8891-9bc2c2076e5f)
# Challenges I met
1.We find a same customer may have different kinds of email which will cause a problem: we send same email content to different account id which belong to the same customer id.This will increase the unsubscribe rate and decrase the performance a lot.
Solution: Group all the account id by the same customer id and set his most frequent account(highest click rate) as his main account.
2.Lots of customer's address are the same but they have different customer and accout id which reveals that they belong to a same family.So sending same email content to different family members is meaningless and will decrease the camapgin's performance.
Solution: Create a familiy bundle campaign and send to the most frequent account of the family which increase the sales and the performance.
# Oppotunities
1.Segement the customer  by the company's original two groups we find that target group's click rate and subscribe rate is much higher than the controlled group.So customized email content is very effective which inspires me a new business opprtunity. Cutomers' behavior, purchacing history and habits will be the crucial guideline for the company's email content.We can segement all the customers into several groups by product category and provide more customized content.
2.Based on some customer's first purchase and the sequent pruchase behavior we can send "buy and save" emali content, give them promotion and discount for their next purchase to increace the retention rate and customer's enagement.
