# Brain-computer-interface using motor imagery
This project was born from a desire with a colleague to compete with the help of brain-computer-interface (BCI)
on various known games (rock paper scissor etc.) We therefore measured our EEG cortical activity
using a 32 channel headset during a homemade protocol combining motor execution and motor imaginary. 
The tasks were to lift and then imagine through 3 different sessions: the left arm, the right arm 
and the right leg.

Ultimately the idea would be to create a real-time BCI able to accurately and robustly classify
the different limb movements and imagined movements to operate commands (rock, paper, scissor) on a
graphical interface.

The first part is an offline study of the recorded EEG signals in order to test different preprocessing
and various classification strategy.
The second part is to perform online analysis and decoding using [MNE-realtime](https://github.com/mne-tools/mne-realtime).

## Experimental setup
The study included two right-handed participant. During the experiments, the subject sat on a 
comfortable chair. Each recording session lasted for about an hour and was divided into: an initial
rest time with eyes closed before fifty loops of a sequence of motor execution followed by motor
imagery as show by the diagram below.

<p align="center">
<img src="docs\readme_img\protocol.png" width="547" height="913">
</p>

There are six experiments including two different paradigms : motor execution (ME) and motor imagery (MI).
One session allow the recording of two experiments for one subject. During one session, a subject 
performs a movement as a first task and imagine it as a second task. The duration of the tasks are 
five seconds and are executed in rhythm with an electronic bell sound.

- 1st session: lifting the **left arm** during 5 sec (ME) then imagining the same movement (MI).
- 2nd session: Same ME and MI task with the **right arm**.
- 3rd session: ME and MI with the **right leg**.

**Material**: A TMSI 32-channel gel headcap was used to record the EEG signal with a 2064 Hz sampling 
frequency. The electrode montage was in  accordance with the standard 5% 10/20 System.

## Offline

### Method
For both ME and MI conditions, the following steps are applied on the raw data in order to remove 
common artifacts and noise:
- Re-referencing monopolar scalp-recorded-EEG signals using an average reference montage.
- Removing the mastoid channels from the analysis.
- Applying a band-pass filter between 2 Hz and 50 Hz and a notch filter on 60 Hz. Filters have to 
be zero-phase (linear phase and delay compensation).
- Rejection of eye blinking, eye movements, heartbeat and muscle artifacts with
Independent Component Analysis (ICA) algorithm. Independent component labelling is automatically done using
[MNE-ICALabel](https://github.com/mne-tools/mne-icalabel).
- Automatic bad channel rejection (based on their correlations and amplitudes). 
Reconstruction of the channels is done by spherical spline interpolation.
- Epoching: Segmentation of the signal into consecutive Epochs of [-150ms; 5000ms] around each event-task.
Baseline correction: Subtraction of the baseline average value is applied to all the epochs.
- Finally bad epochs are automatically rejected using the adaptative threshold computed by [Autoreject](https://autoreject.github.io/stable/index.html).

### Classification scores

#### Intra-subjects

#### Inter-subjects

## Online

### Method

### Classification scores

#### Intra-subjects

#### Inter-subjects

### Video/Gif
Video/Gif of the online preprocessing and classification.