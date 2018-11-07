# Go Nogo

This task is a Go-Nogo Task in which subjects have to respond as quickly as possible to target stimuli and withhold responses to distractor (non-target) stimuli. 

It is typically used to measure inhibitory control, specifically response inhibition.

A basic version is coded here:

		Target Stimulus: blue circle
		Non-Target Stimulus: yellow circle
		Stimulus Presentation Time (SPT): 300 milliseconds
		Inter-Stimulus Intervals (ISI): 900 milliseconds
		Target Probability:20%
		80 Trials per Block: 16 Target, 64 Non-Target
		2 Blocks

Participants first take part in a practise session of 10 trials (2 Target, 8 Non-Target) and must achieve 80% accuracy, or they will undertake the practise trials again. 
 
You can skip the Practise Trials if wanted when you start the experiment (there is an option after Subject and Session)

**"InitialiseVariables"**: At the top of the code tree there is an inline-code  which initialises the TrialIndex and total Accuracy ("TrialIdx" & "totalACC") for the practise trials and the block count ("BlockNum") for the experimentla trials. 

		It also states the Variables:
		Total Block Number ("totalBlock"), which can be changed to increase the number of blocks.
		&
		Sets the stimuli and fixation cross duration attributes for the whole experiment ("StimDur", "FixDur1" and "FixDur2")

		Please note that the fixation cross is split into two so that time is allowed in the trial 
		for a response after the stimulus, and so the block doesnt start with a letter immediately. 

		So, FixDur2 is 700ms, which together with 300ms StimDur makes 1000ms (1s) until end of trial,
		and means we can set "Time Limit" for response to 1000ms in Stimulus Properties.  
		FixDur1 is 200ms, wihich together with FixDur2 (700ms) makes 900ms, or the ISI

**NB:** The number of trials per Block can be changed by double clicking on the "ExpTrialList" object. To increase the number of trials, increase the "weight", but keep the same proportion. e.g. to double it to 160 trials from 80, put in 32 for Target and 128 for NonTarget in weights. 

**NB:** The Display Device Properties is set to "Match Desktop Resolution at Runtime = Yes". If you experience problems with this, please doube click on the "Experiment (GoNogo.es2)" at the top of the code tree and go to the devices tab. cClick on "Display" and click "Edit". Then change "Match Desktop Resolution at Runtime = Yes" to "No" and put in the resolution of your device/screen. 

*Based On:* 

Mehrnaz Rezvanfard, Mehrshad Golesorkhi, Ensieh Ghassemian, Hooman Safaei, Aiden Nasiri Eghbali, Hanieh Alizadeh, Hamed Ekhtiari. (2016). Evaluation of Inhibition Response Behaviour Using the Go/No-Go Paradigm in Normal Individuals: Effects of Variations in the Task Design. Acta Neuropsychologia. Vol. 14, No. 4, 2016, 357-366

(their Go/No-Go tasks were developed using E-Prime V.2 software)
