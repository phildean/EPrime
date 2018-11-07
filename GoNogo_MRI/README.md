# Go Nogo MRI

This is indentical to the GoNogo Task but with some adaptations for MRI

This task is a Go-Nogo Task in which subjects have to respond as quickly as possible to target stimuli and withhold responses to distractor (non-target) stimuli. 

It is typically used to measure inhibitory control, specifically response inhibition.

A basic version is coded here, but with additions for running with MRI:

		Target Stimulus: blue circle
		Non-Target Stimulus: yellow circle
		Stimulus Presentation Time (SPT): 300 milliseconds
		Inter-Stimulus Intervals (ISI): 900 milliseconds
		Target Probability:20%
		80 Trials per Block: 16 Target, 64 Non-Target
		2 Blocks

MRI Additions:

		**"WaitScanner"** added which waits for the first MRI pulse before starting the experiment. 
		The code for this MRI pulse is written in "InitialiseVariables", 
		and is currently set to left Mouse Button press ("1"). 

		**Jitter Nested List** Added. This has values: 100; 150, 200, 250 and 300 
		so the mean is still 200 ms (See FixDur1 below). 
		[FixDur1] is replaced with the atttibute [Jitter] in ExpFixationCross1 
		to allow this jitter during the experiment. 
		If not wnated, change this back to [FixDur1].

		**Timing Information (Run, Event, Onset, Duretion)** is collected 
		and outputted for each subject as a text file  
		"OnsetTimes_$.txt", where $ is the subject number (e.g. OnsetTimes_1.txt for Subject 1).

		**"GetScanPulse"** is added after "WaitScanner" to get the time of the MRI Pulse
		and add it to the variable "StartTimeStamp"

		**Cumulative Timing**: The Timing modes of the experimental slides (fixation crosses and stimulus,
		Block Instruct and EndBlock) are changed from "Event" to "Cumulative" 
		this is to ensure that the MRI scan ends when expected (ie overall time in experiment is constant).

		The "BlockInstruct" and "EndBlock" are now set to a specific time (2s) 
		and does not wait for response. 
		This is to ensure overall experimental time is constant. 

		In ExpStimulus the **"Duration"** Property is ticked in the Logging Tab 
		of the Properties in order to use in the "OnsetTimes" file.

		**"WriteTimingInfo"** is put after the last fixation cross at the end of the trial. 
		This writes the timing information to the "OnsetTimes" text file. 

		The **"PreRelease"** of the "ExpFixationCross2" is set to 30ms so that the inline code
		isnt run during the time a subject can make a response during the PreRelease period. 
		This would mean that the timing information is written to the logfile but no response 
		had been logged and so would be incorrect information. 
		30ms is a compromise as by 970ms after the stimulus (1000-30) subjects should have responded,
		but there would be no time drift as the next object would have time to load. 


Participants first take part in a practise session of 10 trials (2 Target, 8 Non-Target) and must achieve 80% accuracy, or they will undertake the practise trials again. 
 
You can skip the Practise Trials if wanted when you start the experiment (there is an option after Subject and Session)

**"InitialiseVariables":** At the top of the code tree there is an inline-code which initialises the TrialIndex and total Accuracy ("TrialIdx" & "totalACC") for the practise trials and the block count ("BlockNum") for the experimentla trials. 

		It also states the Variables:
		Total Block Number ("totalBlock"), which can be changed to increase the number of blocks.
		&
		Sets the stimuli and fixation cross duration attributes for the whole experiment 
		("StimDur", "FixDur1" and "FixDur2")

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
