# Behavior Question:

## Notes

### STAR:

Situation（情景）：我们需要开发一个新项目/我们某个功能出问题了。

Our product have serious performance issue. A single page take minute to load.

Task（任务）：我觉得这个机会很好，自告奋勇来解决xxx问题。

同时体现下自己契合公司的文化，比如说你面试Facebook，脸书比较看重你工作的Impact，你就可以说: If the page is slow, users will be unsatisfied with our product. I believe improving the performance will have huge impact on our product. So I take this job to investigate the issue.

Action（行动）：我分析了一下产品需求/问题症结，研究了一下目前的代码和业界通用的代码，我觉得问题出在xxx。然后我写了一些脚本对整个生命周期进行分析，做了大量测试，发现确实问题在xxx，一般针对这种问题，我们有几种解决办法，考虑到我们的情况，我做了xxxx, xxxx改进。

Result（结果）：最后速度是以前的xx倍，而且我的方案作为best practice被大家认可，推广

## Questions

### Low Performer

1. Identify the issue,
   1. are they slow to complete the project or does he fail to complete the project, does he consist introduce bug ? it is very important to identify which one is the case.
2. Identify the cost of the low performer
   1. Whether it is their fault or not their fault?
   2. For example:&#x20;
      1. The project is way exceed their level, a junior sde got task from senior .
      2. it is tech debt, unfair to blame engineer&#x20;
      3. External depenedency fail to deliever,&#x20;
      4. Rest of team fail to communicate
      5. Not ask for help when they should
      6. They are just not good&#x20;
   3. You can not determine if he is the low performer based on pr request.
   4. **What we should do?**
      1. It looks like you take a bit of time on the project. is there anything holds you down?
      2. Offer your help, make urself available to them,
      3. If it is no improvement proceed, then  you need to bring issue to your manager.

### Team Confilct

As a matter of fact, there was one in my team. My team have been working on a huge feature , and about to lauch in two weeks away.We finished the feature and ready to ship it. But on thursday afternoon,  an engineer add a lot of stylistic change, no logic change, just refractor a poorly written, a heavy tech debt. one send and one review have a tense confliction.



how i handle any conflict in the work:

1. I always assume good intent on both party. When someone firm disagree with someone else. They have good intent, they generally think their way is right way for the team for themselevs. The person you have conflict with. it is not here to screw you. They disagree with you is becauase they want the best for the team.
2. always try to common ground,  there is some sort of common ground. they want same thing but they have different way to complete it. I grab two enginner in the room, and have a talk with them. Lets assum we have good intent for each other, lets figure out  what was the actual intent.of both your action. The intent who make the pull request is just improve code base , to make it cleaner.The other person's intent is to minize the risk to introduce the bug right before code base. Both them have good intent, and they suddently saw that. They also found common ground. They both care about improving code base. They both agree that one person change is improtant. Both agree do not want the launch ruined by one bug. In the end, they are agree to push the code later after code freeze.
3. The lesson I learn:
   1. always assume good intent, and find common ground
   2. Better communication help!

### Why do you want to work here?

Three main reason:

* Technical point view. Company have a lot of technical that really excited me. Such as xxxx.How the engineer at Company use xxx in scale production level code.
* Put aside technical stuffs for a bit. i am also really interested in xx company culture. move fast. One thing that fraustrated me is the slowness enginner project i work on. From few peer who work at facebook. The philosophy lauch product is dramatic different. I am really excited about that in facebook.
* Facebook bootcamp.  I read a lot of bootcamp experience. I am really excited to try Work on multiple team before commit one. i have not heard any other company doing that. This is really appealing to me.



### Strong Disagreement

There are many times I disagree with coworkers. I do think that is less meaningful for me to focus on particular disagreement as much as I focus on a general process I follow when I have a disagreement.

The process I follow in three steps, some of them are inspired from Amazon leadership if you are faimilar with.

1. Dig deep, really try to understand all the people who invovle in the disagreement 's idea. There arguments and their stances. You have to understand why they are disagree with and why they came the conclusion. They have to understand why and how you came your my conclusion
   * For example, Someone want to change a piece of code and you dont want to change. You have to understand why they change, why is it gonna be better?  Is it be stylistic better, or more performant, or personal preference, or more consist on current code base?
   * Once you figure reasons, you need to dig deeper to find out why we want this. In some cases, people may think performance might not be matter in this particular cases.
   * One important notes is attack people idea, not people. Attacking people is mean and create unhealth relationship
     * You need to make sure you do not attack others and others do not attack you.
2. Take a step back. See thing in a higher level. Often time, the environment you are in that might influence engineer decision. If you do not look the idea in big picture, you would probably think one person is clearly right. In the enginner view, it would take far too much time, it would worse other part of code base and so on. But if you take the step back, our business is depend on doing this feature then we suddenly we know there is necessary to do this feature.**The team might have priority over engineer level opnion**
3. Despite all the things we do, people still have a big disagreement. In that case, you have two option. One is go with majority vote, or escalate the decision to decision maker such as manager. If you do escalate the decision, You need to make sure they know all the context information.
4. Once decision is made, you have to commit to this decision. You cant hold your grudges. If it does not go your way, you have be able to accept that. You have to move forware as it is your decision to make sure product , team and everything go smoothly
5. Yeah this is how i handle strong disagreement and how i plan to continue handling disagreements at work.

### Sudden Onboarding:

Imagine you and your team are in the middle of a major project at work, with many moving parts, complicated context, a lot of work, etc.. A new software engineer joins your team, and you're tasked with onboarding them; what do you do?

I want to emphasize how important to properly onboard the new engineer. Because if you improperly onboard a new engineer, not only you are give them bad first impression to your team and company, which in ture will give them a bad first experience and cause them unhappy. But also you will be causing a lot of other negative effects to trickle later on on them as a person. They might not able to perform properly and they might just perform poorly. You also have negative impact on you team. Because suddenly you will have to take more work.You have to do the work they supposed to do. This will eventually negatively affect your company.&#x20;

Hopefully you have done some preplanning, you have been preparing for this new engineer

Three things:&#x20;

1. The proper document , this one takes pre-planning. Having a proper documentation for the onboarding aspects of their job like getting new devlopment set up as part of team, knowing where they need to go to access inforation. All these things can be very easily captured in the documentation, It can save you tons of time. There is nothing more frustrating than being a new engineer trying to get your development setup and getting a bunch of errors that nobody knows about, nobody documented anywhere.It just a really bad experience.
2. It is very important to make myself available for any questions they might have, for anything they might need to unblock them. Especially when they are joining a team, like you are in the first few days, first couple of weeks. They are naturally gonna have a lot of questions, you will be able to solve that and help them out. You do not want them to waste half of day or full day to do  something you can fix them in 10 seconds.Overwhelming available is better than underwhelming available
3. You have to very carefully pick a project to work on. Once they set up everything, Let them start them out with one or two very very simple bugs. If you working on frontend, they can have jobs like change color in a button or change some text. Something to make them familiar with code base and overrall development process. Then give them a starter project. It may takes one or two weeks. They are not affecting or not depending on anybody else. But it should ideally that would have a decent amount of affect. In frontend aspect, something that customer has request but that is not super important. Then give them a first big project, You do not want this would be a task to block others task. Something is out of critical path and proper to their level.

### Production Outrage:

Describe a time when you had to deal with an outage at work. How did you handle the situation? What steps did you take after the issue was resolved?

I experienced handful production outrage. The one that I want to talk about here. is actually the very first production outrage. I was last engineer in my team. The product primary pages was just blank. It wasnt loading. Nothing show up. So obviously, for a second, I kind of panicked,Then I compose myself. and here is how i handle this.

1. The first thing is I want to confirm that this was actually a real bug in production , not some bug  on my computer, or my account, or something like that. So I ask a couple people around , These were not  my teammates,  to go on the link of the page and see if they also experience same thing on their computers, on their accounts. And yes they were.
2. Before alerting anyone else,I was gonna spend 5 to 10 minutes to see if i could debug the issue. I wanted to see can i fix it withoput alert my teammate,  It turns out I wasn't able to figure out what the cause of the issue was. It was a very weird bug, blank page, nothing in the chrome console.At that point, I did alert the rest of my team after around 10 minutes. Here is my philosophy to deal with this issue. You never wanna play the hero, if you can try to figure the issue within five minutes, but after a certain point, there is no point for hiding it from other people. The key thing is to fix the issue.
3. One of my team still have chance to fix the problem.One of key thing here that we did  which is something that i am very big proponent of  is Even though the situation is stressful, our landing page is down, so whole product is unusuable. You have to calm you have to not put figure or blame to anybody.Obviously, It is very easy to potentially point fingers and blame people when you say something like this file is poorly written. We do not want to do that. This is unhealthy in a team in general. So we pair program we document everything we do and keep our team in the loop.,At that point our manager was also in the loop. We follow the process that we knew to follow











### Work Distribution

### Past Mistake

### Challenging Project

My XXX project is a React web application. It's the second project on my resume. I implemented a Material UI version of cnodejs.org website, which is the biggest Node.js Chinese community. I applied ReactJS for the Frontend development, which is the most popular Frontend framework. I used Node.js and Express for Backend services development. The difficult/interesting part is that when I wanted to deploy the website on AWS, I found that the generated website JS file was very big up to 900 kilobytes. But I had optimized the generated file according to React official document. To conquer it, I read a lot of source code on GitHub and talk with my friends in the industry and tried for many times（这里透露了三个点：自主学习能力，向合适的的人寻求帮助还有实验精神）. Finally I found the problem which is that I used a third-party react component called "react-simplemde-editor" and its code quality was not good enough. The author of this component used React as the production dependency instead of the development dependency which leads to the big generated JS file. Then I solved the problem by rewriting the component by myself. After this optimization, the generated JS file was reduced by 200 kilobytes. When I seen the website used by thousands of web developers, I was very proud of it.

### Production Outrage

### Tough Feedback

### Strengths and Improvement

### Comfort Zone

### **What do you know about us**

### Where Do You See Yourself in 5 Years?

Well, I’m definitely really excited about the associate consultant position at Midnight Consulting, and I can see myself growing professionally in this role. I think, generally speaking, within the next five years I would seek to make a significant impact at Midnight Consulting, particularly in the energy sector. I’m also looking forward to eventually taking on additional managerial responsibilities and possibly taking the lead on some projects. Another big part of my life is mentoring, so I would hope to incorporate more of that as my knowledge of this industry develops.



### Why are you interested in this position?

### What's your biggest failure? What's your most regretful decision in your work?

What's your biggest failure? What's your most regretful decision in your work?

这种负面问题是最讨厌的，很容易一不小心说多了给面试官留下坏印象，又不能太油滑回避问题。回答原则就是实话实说，说说你过去的失败经历，你犯的错误造成的后果，以及你学到了什么，比如说你可以这样：我曾经领导一个项目（可以是course project, 或者是工作上的项目），带着一堆人，起初我觉得大家都是优秀的工程师，所以开始就简单的做一个计划， 分配好任务就开始做了，做到后面慢慢发现当我们把大家的东西整合到一起的时候，我们发现了很多问题，比如有人默认其他人已经handle好了exception，他就没有再做检查等等。最后我们浪费了不少时间在debug上面。如果让我再做一次，我会花更多的时间在分析上，明确好每个人的责任，定好interface等等再分配任务，这样就能避免很多问题。

我觉得这个例子一般，暂时想不到更好的回答。我在面试中遇到过这个问题，我的回答是结合我自身经历来说的，并不通用，但是回答结构和上面的例子差不多。之后如果有看到更好的例子，会再做补充。

## Question You ask for HR/Manager

* What qualities do you look out for when hiring for this role?
* Can you share more about the day-to-day responsibilities of this position? What's a typical day like?
* If I were hired for this role, what would you want me to achieve in my first months in the position?
* Can you talk about the company culture a bit
* Are there any qualifications that you think I'm missing?

###

