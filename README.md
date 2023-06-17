# AlignmentApproximator

This tutorial document provides a comprehensive guide on how to effectively utilize the Alignment Approximator tool. Our tool, developed as a ProM plug-in in Java, implements a novel method for conformance approximation. ProM, a widely acclaimed framework for Process mining with extensive plug-in support, serves as the foundation for our tool's implementation. The plug-in, known as the Alignment Approximator, can be accessed through the LogFiltering package(svn.win.tue.nl/repos/prom/Packages/LogFiltering). In this document, we will walk you through the process of accessing and using the tool step-by-step.

Tool Installation

Before proceeding, ensure that you have installed the ProM tool. If you haven't done so already, please follow the guidelines provided at https://promtools.org/prom-6-12/ for ProM installation.

1- Download the latest nightly build of ProM 6 from ProM Tools in the form of a tar.gz file from https://promtools.org/prom-6-nightly-builds/.
2- Extract the downloaded file to a designated folder.
3- In the extracted folder, you should find the following files and folders. 
![image](https://github.com/fanisanim/ConformanceApproximator/assets/26930258/e79485ab-fd26-4e7c-8c66-ebd327a01428)
4- Run the package manager from the folder using the PackageManager file (either .bat or .sh).

5- Select the LogFiltering package and proceed to update it. Note that you might need to navigate to the "out of date" tab for this step.
![image](https://github.com/fanisanim/ConformanceApproximator/assets/26930258/8b9a8ddb-15ee-4876-bf76-04b48ed1633b)
6- Close the PackageManager and launch ProM using the ProM file (either .bat or .sh).

Using the Tool

In this section, we will outline the sequence of steps involved in a typical user interaction with the plug-in interface. Each step will be accompanied by an illustrative figure showcasing the current interaction state. Furthermore, we will provide concise descriptions of the expected actions and the required plug-in parameters.
The Alignment Approximator tool can be used in two ways: by providing one event log and a Petri net, or by providing two event logs. In the latter scenario, the second event log represents the process model, with its behavior serving as the sole reference for correct process execution. We will now explain both approaches in detail.

1- Using Event Log and Process Model
The most common scenario involves having an event log and a process model to compute the alignment. Our tool exclusively supports process models in Petri net notation. It's worth noting that ProM offers several plugins for converting process models from various notations to Petri nets. Alternatively, you can discover a process model from the event log for this purpose.

1- Search for the "Alignment Approximator" plug-in and select the first option if you have one event log and a Petri net. The second option is specifically for scenarios involving two event logs. ![image](https://github.com/fanisanim/ConformanceApproximator/assets/26930258/c2667b68-408f-42be-82aa-26c76e22d0e9)

2- In the left pane, you will find two inputs: an event log and a Petri net. Select an event log and a designed or discovered Petri net as inputs. While the Petri net can contain silent transitions or duplicate labels, it must be sound. Note that selecting the inputs will only enable the start button for the first plug-in.
![image](https://github.com/fanisanim/ConformanceApproximator/assets/26930258/4c33a558-c3bc-4046-85d4-59a073cbc06a)

3- Click on the start button.

4-Choose either the "subset selection" or "simulation" method to approximate the alignment. For now, let's assume that the subset selection method is selected.
![image](https://github.com/fanisanim/ConformanceApproximator/assets/26930258/08038cd1-2deb-40ae-a66b-a8113a90fd33)

5- You can now adjust the options for approximating alignment using the subset selection method. For instance, you can determine the percentage of variants you want in the subset. Having more variants generally leads to more accurate approximation at the cost of increased computation time. If all variants are selected, the tool will provide an accurate alignment. Different methods for variant selection are available, such as choosing the most frequent ones or random selection. In typical use cases, selecting between 10 to 20 percent of variants and using Frequency-based selection achieves good accuracy.
![image](https://github.com/fanisanim/ConformanceApproximator/assets/26930258/8d4bcfe1-903d-4b2e-afbd-d20dcadbbed0)

6- The tool will generate the following output: (1) alignment approximation, (2) bounds for the approximation indicating the upper and lower bounds for the actual alignment value, and (3) synchronous and asynchronous moves (along with their rates) for each activity. 
![image](https://github.com/fanisanim/ConformanceApproximator/assets/26930258/672d1d13-0b49-4c89-ab68-524fc0a69e91)

If the simulation method is selected in Step 4, follow these additional steps:
5- Configure the "Simulation Parameters." By default, the plug-in provides a predefined configuration for four parameters, but you can modify them as needed. The parameters include the maximum number of traces to be simulated (representing the desired number of unique traces), and the subsequence length used to compute the occurrence probabilities of simulated traces. For detailed information on this method, refer to https://www.researchgate.net/publication/352312288_Conformance_Checking_Approximation_through_a_Process_Model_Simulation_-_Master_Thesis. 
![image](https://github.com/fanisanim/ConformanceApproximator/assets/26930258/0a38249b-b626-43a8-9bd1-6a2769a0975d)

6- The output structure will be similar to the previous method, yielding the following results:
![image](https://github.com/fanisanim/ConformanceApproximator/assets/26930258/c936026f-01ec-4cd1-86ee-bb2730b5dab3)


2- Using Two Event Logs

One of the key advantages of our tool is its ability to compute (approximate) the alignment cost without requiring a process model in common notations. Instead, we can treat an event log and its behavior as a process model. To achieve this, the Alignment Approximator expects two event logs as inputs, with the second event log representing the process model.
In the provided figure, you can see the ProM interface with two event logs selected as input.
![image](https://github.com/fanisanim/ConformanceApproximator/assets/26930258/a394dcc3-e833-4dd3-959f-021472a125f0)

Approximating alignment using this method does not require any further user adjustment, and the output structure remains the same as described earlier.
![image](https://github.com/fanisanim/ConformanceApproximator/assets/26930258/c1418ba2-800d-4e9e-aa2b-fba1de4a1d55)


Please note that there are various ways to generate a process model in event log format. You can choose to select/sample specific variants or traces from an event log, or simulate a process model to obtain an event log.
