# Continuous Performance Task (CPT)

This task is a Continuous Performance Task (CPT), in which participants must maintain constant focus on a string of task stimuli. Typically, they must reponsd ro (rare) target stimuli (CPT-X) or combinations of stimuli (CPT-AX), and not respond to (frequent) non-target stimuli. 

It is typically used to measure sustained (or selective) attention. 

A basic CPT-X is coded here:

		Target Stimulus: X
		Non-Target Stimulus: A Random pick from all other leters of the alphabet
		Stimulus Presentation Time (SPT): 250 milliseconds
		Inter-Stimulus Intervals (ISI): 1000 milliseconds
		Target Probability:25%
		20 Trials per Block: 5 Target, 15 Non-Target
		9 Blocks

Participants first take part in a practise session of 8 trials (2 Target, 6 Non-Target) and must achieve 50% accuracy, or they will undertake the practise trials again. 
 
You can skip the Practise Trials if wanted when you start the experiment (there is an option after Subject and Session)

**"InitialiseVariables"**:  At the top of the code tree there is an inline-code which initialises the TrialIndex and total Accuracy ("TrialIdx" & "totalACC") for the practise trials.

		It also sets the stimuli and fixation cross duration attributes for the whole experiment 
		("StimDur", "FixDur1" and "FixDur2")

		Please note that the fixation cross is split into two so that time is allowed in the trial 
		for a response after the stimulus, and so the block doesnt start with a letter immediately. 

		So, FixDur2 is 750ms, which together with 250ms StimDur makes 1000ms (1s) until end of trial,
		and means we can set "Time Limit" for response to 1000ms in Stimulus Properties.  
		FixDur1 is 250ms, which together with FixDur2 (750ms) makes 1000ms, or the ISI

**NB:** This task is coded differently to the GoNogo with respect to how Blocks are repeated. The Number of Blocks is determined by the "cycle" property of "ExpBlockList". To change the number of blocks,cdouble click on "ExpBlockList", click on properties (the picture of the hand and paper) and click on the Reset/Exit tab. Change the number of cycles here from 9 to any other figure to change block number. 

**NB:** The number of trials per Block can be changed by double clicking on the "ExpTrialList" object. To increase the number of trials, increase the "weight", but keep the same proportion. e.g. to double it to 40 trials from 20, put in 10 for Target and 30 for NonTarget in weights. 

**NB:** The Display Device Properties is set to "Match Desktop Resolution at Runtime = Yes". If you experience problems with this, please doube click on the "Experiment (GoNogo.es2)" at the top of the code tree and go to the devices tab. cClick on "Display" and click "Edit". Then change "Match Desktop Resolution at Runtime = Yes" to "No" and put in the resolution of your device/screen. 

*Based on:*

Jay K. Brinker, Mel Campisi, Laura Gibbs, Rebekah Izzard (2015). Rumination, Mood and Cognitive Performance.Psychology, 2013. Vol.4, No.3A, 224-231

