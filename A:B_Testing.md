# Clarify Context
情景假设:
On an online vedio platform, recently your team conducted a reasearch and found that video playtime negatively correlates with observed latency of the loading pages. What's your recommendation to the product team?
**Correlation != Causality** correlation存在causality的可能性
correlation：观测出的结果
causality：实验证明得出

## 提问题
In business world, questions are different. Serveral perspectives need to be considered.
* What?
* Why? Does it worth?

According to our specific example, what kind of question we could ask:
* How do you define latency?
* Why watch time matters?
* Scope of this problem?
	* Global or specific country?
	* How many users are impacted? 

# Make Hypothesis
* What do you think might be the reasons?(面试前去了解公司、产品)
	* First of all, assume causality(i.e. higher latency -> less likely to watch)
	* Justify with one or several valid reason

# Design Experiment
* Hypothesis: Higher latency is bad user experience and is preventing user from watching. So, if we reduce latency, our users will watch more videos. 
* There are threee steps for this:
	## Determine Metric: select one "success metric" that your experiment will be measured against. 
	For our example particular, the metric would be the watching time of users.
    1. AARM Framework:
		* Acquisition: For our example particular, the metric would be the watching time of users --> Number of users who signed up(只是注册)
		* Activation: User takes some key actions to be "active" --> Number of users who watched XX minutes in last month(多少用户观看了视频)(FB加了10个好友留存率就会变多)
		* Retention: User continues to use the service --> Number of active users
		* Monetization: User pays. Total revenue, ARPU --> Revenue/Subscribers(Buy membership)
	2. North Star Metric(言之有理):
		Sample answer: number of watch minutes. Watching video is a key action that matters at YouTube, so I'd like to choose a metric that can reflect level of watching activities in aggregate. 
	3. Sanity Check: it would be good to talk about doing sanity check on the metric. Why it make sense?(购买次数VS购买金额)
		* The distribution looks ok(something like bell curve)
		* Not too volatile(small standard deviation). It's hard to detect impact(smaller power) on a noisier metric.
	## Design Experiment(Design A/B Test)设计实验
	### Choose population
	#### Choose targeting population
	* Target only the relevant users
	* Why? Lots of noise, and result will be highly diluted.
	* How?
    	* Before-fact: PM/SDE inputs
    	* Triggering: only when user see something
    	* Post-fact: slice data by the eligibility criteria
	#### Particular for our example:
	* Which countries?
	* If we expose this feature to certain videos only. How do you know who have seen it?

	### Choose cohort as population
	* Let's define "cohort": tract the same group of users over time. 
    	* Track Population: 
        	* Who ever joined: quick, on the spot.
      	* Track Cohort: sample group of users with learning effects
        	* Retention
        	* Adoption of a new feature(novelty effect)
        	* Run longer: dosage over time. e.g. "wanna watch?"
	### Determine sample size
	* Standard Error ~ 1/sqrt(n)
	* Large sample size, always better
	* But running a large sample size has some drawbacks
    	* Max allowable size: 50%
    	* Save space, growth hacking, rapid develop
  	* So, we want the smallest possible experiment size to achieve maximum. 
	### Sampling method
	* Simple
    	* Every user has equal chance of likelihood of being selected
    	* Stratified
        	* Problem: only 1% of our users are high spenders
        	* Strata: low/medium/high spender
        	* Ensures that an equal representation from each strata
	### Experiment Duration
	* Duration vs. Exposure
    	* Duration: # of days you want it to run
    	* Exposure: % of users who see this experiment on a day
    	* Duration * Exposure: N
    	* Duration and exposure are trade-offs.
    	* Exercise: why not load everything on the same day?
  			(1. Reduce seasonality; 2. Reduce risk)
	
	## Interpret Restuls
	**This is where you make recommendation so it is important!**
	* Briefly describe how to calculate hypothesis testing
    	* (Almost always)Two sample t-tests
    	* Calculate t-score
    	* State your decision criteria
	
	## Make Recommendation
	* Not statistic significant?
    	* What have we learned?
  	* Statistic significant?
    	* Good, but talk about trade-offs
    	* Benefit: small impact
    	* Cost: hard to implement
    	* Opportunity cost:(Prioritization)