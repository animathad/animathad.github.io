---
title: "Non-Profit Product Management: Silicon valley tech for the Good"
tags: [life, nonprofit, product, product design, product management]
description: "My journey, building a product for Non-Profits. Who ? I got a chance to be a Product Manager Fellow for TFI. TFI helps build products for Non-Profits.…"
original_date: 2018-01-31T06:27:15-08:00
---

My journey, building a product for Non-Profits.

### Who ?

I got a chance to be a Product Manager Fellow for [TFI](https://www.tfi-fellowship.org). TFI helps build products for Non-Profits. Every summer around 4–5 projects are executed with the help of PM Fellows & Engineering Intern. The cause is to solve the problems Non-Profits’ face with latest technology and sustainable execution.

[![](/assets/img/posts/non-profit-product-management-silicon-valley-tech-for-the-good/1-d5wmQtCd5d1JaoKRjHEFIg.png)](http://littlebrotherssf.org)

One such non-profit is [Little Brothers Friends of the Elderly](http://littlebrotherssf.org). They help lonely elders in the Bay Area. Volunteers sign up as the “Little Brother” who visit their “matched” elders on holidays, birthdays or every other week.

### What problem was being solved ?

LBFE was having issues tracking volunteer hours. Volunteers didn’t check-in their visits or LBFE had no way of knowing how many volunteers are active and visiting. LBFE needed these hours for two main reasons:

1. To keep a check on elders’ emotional health
2. Measure LBFE’s impact to raise funds to help more elders

### Lifecycle of the Product ?

The App was called Rendezvous: A *meeting at an agreed time and place, typically between two people.*

**User Surveys**

![](/assets/img/posts/non-profit-product-management-silicon-valley-tech-for-the-good/1-kn4I-n7hLZB7q4IrwX2ORQ.jpeg)

Luckily we had power users to our rescue. Upon various phone calls and in-person interviews we found that:

1. Volunteers didn’t know they have to check-in. The periodic emails sent out was not catching their attention and the emails were confusing. #Communication
2. Volunteers didn’t have one place to check-in and emails were too clunky to “check-in”. #SmellsLikeMobileApp
3. Some users became close to the elders and forgot who connected them. This made LBFE irrelevant for them. #Moat 🙂 ?
4. There was no motivation to respond. Why should I ? What do you want to do with that data ? #UserEngagement #Trust
5. Many users did this “job” because their company gave them some perks. They definitely wanted a tool to pull their hours for easy submission #ComputePower
6. LBFE wanted one place to monitor the elders. Volunteers would be the ideal feeders to this app. The other benefit would of course be data for fund raising. LBFE loved if there could be engagement and get users back for the visits.

**The Ideal Product**

![](/assets/img/posts/non-profit-product-management-silicon-valley-tech-for-the-good/1-XXhXuPA8zfJyrLrEZWAr7A.jpeg)

I wanted to be the next Steve Jobs of Non-Profit products! I had a dream to build a social, engaging facebook equivalent social network. I had already thought about blasting the designers for not having rounded edges in the rectangles! I could see myself talking to engineers, showing them how it is done. In my dreams I was building features upon features in one weekend and rubbing it in their faces. After the launch I had already seen the app scale to a million volunteers and the technology stack just seemlessly handled the traffic. It was like the Uber App, All I needed to do was may be enable geo location …. **And then I woke up.**

**What I really had**

![](/assets/img/posts/non-profit-product-management-silicon-valley-tech-for-the-good/1-EplBuZiSAuxAJUl26eedWw.jpeg)

1. No Budget! Zero! Zilch! 0
2. I had 4 interns. One of them quit after the first week of my speech! Another hadn’t done any coding. The other two were fairly decent. I was on my own for the designers
3. I had 3 months. After 3 months, the App should be on zero maintenance mode.
4. The Bright side: **I had a customer!**

> Building for an existing customer and problem case is bliss!

**Vicissitudes of Life**

Once I hit the ground from my dream clouds. I really was grounded and set my expectations low. The hardest part was to lower the expectations of LBFE because I had promised them too much.

**Hosting Services**

The hosting problem was solved thanks to Microsoft Azure. They generously offer 5,000$ credits to Non-Profits (who would have thought the former Darth Vader of Tech would do such a kind thing!)

**Design**

- App had a simple form to fill check-in data

![](/assets/img/posts/non-profit-product-management-silicon-valley-tech-for-the-good/1-2Mz1DIpjdcH6avKA6MPtDA.jpeg)

- There were karma points and badges that could be earned for every checkin. This was the gamification strategy.

![](/assets/img/posts/non-profit-product-management-silicon-valley-tech-for-the-good/1-kX4YS5knMNKbP-PGeBMpbA.png)

- A leadership board to encourage more volunteer hours
- Login & Registration was through email, magic link etc.
- LBFE would pull data from the backend to get reports

I sketched a very basic checkin webapp. Since we didn’t have money to host anything. Iphone Apps and other things were out of question.

Midway into the project, I got a really talented designer. One of the nicest persons I have met. Had given me wonderful insights into making the Web App intuitive and engaging. But it was too late in the project to bring it in. I could borrow some of the icons and workflow transitions.

**Technology**

The plan was to create a Web Application (NodeJS + MongoDB) hosted on Microsoft Azure.

**Engineers**

So when it comes to Engineering; I had one genius programmer and 2 other were humble learners. Keeping people motivated is hard in a Non-Profit endeavour. I had to give pep talks every week. But the really genius don’t buy it! And it is either my way or the highway for them. Since I had an engineering background, I wanted to architect and mentor the Interns. But the genius programmer had his own ideas. He also lacked the empathy to come down to the mortals and play well. I felt this was pretty much the end of the product. My assumption was the bright one will lead the gang. I could do my job.

> With great minds comes great egos!

![](/assets/img/posts/non-profit-product-management-silicon-valley-tech-for-the-good/1-XPh9zx6OLN-VHr3p9JS0YQ.jpeg)

My guidance were constantly modified and detoured. I asked Mongo I got MySQL. I said Node he said Python! I tried to be respectful to not hurt sentiments. I became a push over and was in pleasing mode.

At some point I had to put my foot down and jumped into specifics of “how”. I had 2 weeks of no communication. Since this was part time for everyone. Such delays and asynchronous communications were supposed to be normal. 2 months into the project the genius boy stopped working. I hurt his ego too much when I got into his “territory”.

Now I have 1 month, two humble hungry students whose only take away form this project was learning, and the idea of helping a non-profit. I had to bite the bullet again and convince the genius boy to get on track (or get on his track).

**Show Time!**

![](/assets/img/posts/non-profit-product-management-silicon-valley-tech-for-the-good/1-SPfiwRVmDInSfkAxtHcctQ.jpeg)

We did get a demoable App for presentation day. It was not exactly how I wanted it. The other interns didn’t learn anything because of the pace of the genius boy. But customers didn’t use it. **So the product failed!**

### **What I would have done differently ?**

![](/assets/img/posts/non-profit-product-management-silicon-valley-tech-for-the-good/1-jTuZHksvfijYBFm-xAH0bg.jpeg)

- **Psyche**: I always thought PM’s should be non-authoratative. But that doesn’t mean to be be a push over. I should have been assertive.
- **Ego Management**: There is no point having a rockstart programmer on the team if he doesn’t build what you want. I would have taken control of the leading the engineers from the beginning. I had the plan in my mind. I needed engineers to execute it. In a professional project, I could escalate it to the Engineering Manager and wouldn’t have faced this issue.
- **Bare Bones/MVP:** I would take several steps back. I should have created a simple online survey/form. I could have leveraged the power users to give feedback. May be made that public. I was biased to build a Web App. The time frame of 3 months created a pressure which played games on my mind.

### **Learnings**

![](/assets/img/posts/non-profit-product-management-silicon-valley-tech-for-the-good/1-Zf2nEr2v5-vFnX4CH5yLaw.jpeg)

- Say No! Be Assertive but humble.
- Leadership is also about correcting the wrong. You can’t make everyone happy. I let down 3 people on the team and my customers to be nice to one person. The cost of pleasing one person is too heavy.
- I now have a lot of biases 🙂

> Start from the bare minimum and stay on bare minimum!

- Be a minimalist. Stay on excel sheets, forms, etc. depending on your budget
- Be Customer Obsessed. Keep customers in touch with any bare minimum “product” to stay focused.
