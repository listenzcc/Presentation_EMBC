# Temporal Dynamics on Decoding Target Stimuli in Rapid Serial Visual Presentation using Magnetoencephalography

- [Temporal Dynamics on Decoding Target Stimuli in Rapid Serial Visual Presentation using Magnetoencephalography](#temporal-dynamics-on-decoding-target-stimuli-in-rapid-serial-visual-presentation-using-magnetoencephalography)
  - [Title page](#title-page)
  - [Table of contents](#table-of-contents)
  - [Introduction](#introduction)
    - [Background](#background)
    - [Motivation](#motivation)
    - [This work](#this-work)
  - [Experiment and Methods](#experiment-and-methods)
    - [Experiment Design](#experiment-design)
    - [MEG and MRI acquisition](#meg-and-mri-acquisition)
    - [Cortical Neuronal Activation Estimation](#cortical-neuronal-activation-estimation)
    - [MEG Preprocessing](#meg-preprocessing)
    - [MVPA](#mvpa)
  - [Results](#results)
    - [MEG Signal Visualization](#meg-signal-visualization)
    - [Cortical Neuronal Activation 1](#cortical-neuronal-activation-1)
    - [Cortical Neuronal Activation 2](#cortical-neuronal-activation-2)
    - [MVPA scores 1](#mvpa-scores-1)
    - [MVPA scores 2](#mvpa-scores-2)
    - [MVPA scores 3](#mvpa-scores-3)
  - [Conclusion and Acknowledgements](#conclusion-and-acknowledgements)
    - [Conclusion](#conclusion)
    - [Acknowledgements](#acknowledgements)

## Title page

Hello, I am Chuncheng Zhang from Institute of Automation, Chinese Academy of Science

Appreciate EMBC communicate to give me the opportunity to share my recent work.

The subject I want to share today is Temporal Dynamics on Decoding Target Stimuli in Rapid Serial Visual Presentation using Magnetoencephalography.

## Table of contents

I would like to give the presentation in four part, Introduction, Experiment and Methods, Results and Conclusion.

## Introduction

Let's start with Introduction part.

### Background

Rapid serial visual presentation, known as RSVP, is a high efficient BCI paradigm.
It has been applied in many areas such as data categorization, face recognition, speller and website evaluation.

- RSVP uses odd-ball effect, when present a rapid serial to a subject, the odd-ball stimuli will trigger certain event-related neural response.
  Since the event-related response can be detected, we can select the odd-ball stimuli based on the signal detection.
- If we have a sequence of stimulus with some odd-ball in it, but we don't know where they are exactly.
  So we present the sequence in rapid serial to a subject and record his neural response.
  Then we can find the odd-balls by detecting event-related response.
  That is the classic application of RSVP experiment.

### Motivation

We already know the fact of odd-ball stimuli can trigger event-related neural response.
And the detection of event-related response is key to RSVP-BCI application.

However, the temporal dynamic of discriminate power and underlying neural activity is still unclear.

(CLICK)

As a result, the motivation of this work is to investigate them.

### This work

In this work,

1. We performed RSVP experiment, recorded MEG data when rapid serial was presenting, and took paired MRI image.
2. We investigate underlying neural activity using paired analysis of MEG and MRI.
3. We investigate the temporal dynamic of discriminate power using MVPA method under different frequency bands.

## Experiment and Methods

Next, I will introduce the process of experiment and analysis methods briefly.

### Experiment Design

For the RSVP experiment,

- We recruited 10 college students, their ages are around 23 years old.
- Every participant perform 10 blocks RSVP experiments.
- In RSVP experiment, we present the subject with street-view pictures, the pictures containing human were considered as target pictures (the so-called odd-balls).
- In each block, 100 pictures were shown in random order at a rate of 10 Hz.
- The chance of target pictures was set to 4 percent.
- The pictures in below are the examples of target and non-target.

### MEG and MRI acquisition

All the RSVP experiments were in MEG scanner,

- The participant sat in the scanner and the screen in front of them showing the stimuli pictures.
- The MEG scanning used a whole-head CTF MEG system with 272 channels.

Immediately after RSVP experiment,

- We took the MRI image of the brain using a 3.0 Tesla MRI scanner.
- To make sure we can align the MEG and MRI images, we marked three points on subject's nose and ears.

The right picture shows how the MEG and MRI images were aligned using the markers.

### Cortical Neuronal Activation Estimation

Based on the paired MEG and MRI data, we estimated the cortical neuronal activation.

1. The subject-specific cortical surfaces were build based on the MRI data using freesurfer software.
2. Then a forward model was calculated to project the MEG data into cortical surfaces using the 'oct6' space.

### MEG Preprocessing

The MEG data were preprocessed using MNE software.

1. We suppressing artificial noise using ICA decomposition method.
2. Then the signal were filtered into different bands for further analysis.

   - The filter bands were three classic ones, Alpha, Theta and Delta bands.
   - And two custom bands were also used in this work, they are U30 and U07 bands.

### MVPA

The processed MEG data were then analysed using MVPA method.

1. Firstly, the data were separated into training and testing set.
   The separation used 10-folder cross validation method.
   In each folder, data from one block were used as testing set and others were used as training set.
2. Secondly, to enhance the signal-to-noisy rate, we training a xDAWN spatial filter, the number of components were set to 6.
   The signal were filtered by the xDAWN filter to perform feature extraction.
3. Thirdly, SVM classifier with RBF kernel was trained.
4. Eventually, the testing set was used to validate the classifier.
   As a result, we can obtain discriminate power based on the classification results.

## Results

Then, let me show the results.

### MEG Signal Visualization

Here we present the event-related response of target pictures.

- Note that it is the average signal of all the target response.
- The time limit is set from negative 0.2 seconds to positive 1.2 seconds to the onset time.

Two facts can be obtained from the waveform,

1. In U07 band, the waveform reaches its peak at around 0.4 seconds.
2. In U30 band, the waveform shows the same trend plus some high-frequency components.

### Cortical Neuronal Activation 1

For the cortical neuronal activation Visualization, we show the activation on cortex surface.

- We show a bottom-up view since the activation is mainly on FFA and MT areas,
  which is Fusiform Face Area and Temporal cortex.

- You can also say it is the ventral part of visual path way,
  which is widely known as processing the context of visual stimuli.

### Cortical Neuronal Activation 2

Here, we also show the waveform of several brain areas.

### MVPA scores 1

To evaluation the discriminate power of target stimuli,

- We used several measurements of the classification results, they are Recall-score, f1-score and Accuracy-score,
- In simple word, the higher value means the more confident we have when the classifier says it detect a target.
- For the target picture,
  - The Recall score refers the ratio of the true positive in all the detected pictures;
  - The f1 score refers the overall accuracy of the target detected.

### MVPA scores 2

We present the scores in bar graphs,

- The colored lines and starts on the top refers the different between the two bars is significantly high according to p-value of t-test.
- It shows that the lower frequency components yield higher discriminate power.

The accuracy score is relatively higher than the other two is because that, the non-target pictures is largely out number the targets,

Also because of the imbalance of the numbers of target and non-target pictures,

- The chance level of f1-score is NOT 0.5,
- The dash line in figure a) is just for comparable for others.

### MVPA scores 3

We present time-windowed MVPA results in this page,

- The colored curves refer the temporal dynamic of scores,
- The colored lines above refer the scores at these time points are significant larger than chance level according to p-value of t-test.

Look at the black and yellow curves,

- The bands of U07 and U30 also shows the highest discriminate power.

- Recall that the waveform reaches peak at around 0.4 seconds after onset,
  The scores also reaches peak at the same time.

## Conclusion and Acknowledgements

Here we come to the conclusion.

### Conclusion

There are three conclusion on this work,

1. The temporal dynamic of RSVP target response was investigated using MEG signal with different frequency bands.
2. The MVPA results showed that the U07 band signals yielded highest decoding accuracy, and further uncover the decoding power dynamic reached its peak at around 0.4 second after target stimuli onset.
3. The cortical neuronal activation identified the regions that being activated by target pictures, like temporal cortex and fusiform area.

### Acknowledgements

Lastly, I would like to appreciate the EMBC community again to give me the chance to share my work.

And appreciate the grants that support the work.
