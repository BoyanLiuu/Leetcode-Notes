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

### Sudden Onboarding

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

