---
layout: post
title: "research_papers"
date: 1970-01-01
---



======  Comparison of virtual frameworks with respect to sensor data ======



Abstract In this overview paper, we analyse the various virtual reality platform with respect to the sensor data. The quality of the sensor data is compared with the real world in making the final assumption of the quality of the data obtained from the sensor models. An overview of the sensor models, the ease of binding them in the virtual environment, their data format is also analysed.

Introduction

Due to the availability of different virutal enviornment, it is interesting to know the benchmarks in the ease of obtaining the sensor data information from them. This information is helpful for researchers who would like to pick up the virtual environment best suited for their work. Various criterias such as computing resource, quality of the sensor data, reliability of the sensor data, ease of procuring the sensor data from the virtual environment is important for the researchers before they choose the right virtual environment and the sensor model.

Test Object

The following are the list of the virtual environment that has been tested. • V-REP • Gazebo • VIRES • CarMaker Various Sensor models are created in the simuation environment. This is the list of the tested sensor models • Proximity Sensors • Vision Sensors • Velodyne LIDAR • RADAR Sensors The critieras for testing the systems are as follows: 





====== A real-time multisensor fusion fitness framework for advanced driver assistance systems ======

Abstract 

The reliablility of automotive features is directly dependant on the fitness of the sensor-data. Citation needed. EAES is a project whose purpose is to analyse the fitness landscape of various sensors, before they are fed to the controllers for the execution of the underlying algorithm. In this project, we strive to come up with analysis of current algorithms with respect to their iteration time, efficiency and influence of the sensor-data in realising the safety-critical functions. The study would assist in paving a path for the certification of multi-sensor fusion algorithms and optimising benchmarks that could give rating to various algorithms or frameworks for their efficiency of the successful usage of these sensor-data. Lastly, the new algorithms designed in this project, would help in pushing the marker of the reliability index to an improved level. 


In our paper, we present an algorithm to automatically mix the fitness landscape of various sensors depending on the environment conditions. The need of such a fitness landscape is because different sensors behave differently in different environmental conditions. Citation needed
We also show two more alorithms that would generate offline and online decision trees in different test scenarios vis a vis different weather conditions. 
Finally, an experimental test bench is shown.

Introduction

Our software WeatherNeffects uses the existing sensor fusion platforms and makes a robust system against adverse weather conditions. The motivation to write such a software, was done because there are many softwares in the field of robotics such as VREP, Computer Graphics such as OpenCL, but a software dedicated to handle weather conditions does not exist yet. Citation needed. 

The software generates weather simulation on virtual reality platform and and uses it to test the ADAS functionality. The software combines the different sensors and produces an offline priority tree, to determine which sensor is best fit to be used in a particular condition. In the second phase, the software minimizes the effects of weather by machine learning the environment beforehand and using the scenario for reliable calculations. The idea is to further help the Advanced Driver Assistance System in making the right decisions in adverse weather conditions. 

This paper is divided into following sections. 

In the first section, the fitness landscape is extracted from the different parameters and their importance is discussed. We also see if deadlines can be met at the time of using these values. 

In the subsequent section, these fitness landscapes are overlapped with each other to generate an offline decision tree, so that right sensors could be mixed with each other depending on the different environment conditions. 

In the next section, we elaborate the use of online priority decision tree

In the last section we discuss the probable use cases / experiments pertaining to the features in ADAS. We discuss here the probable use cases / experiments pertaining to the features in ADAS. 

Proposal

This paper proposes a novel idea to eliminate all the uncertainities prior to feeding the data into the controllers. This reduces the sensor dataset to a relatively compacter dataset and hence help in a speedy execution of the algorithms running in the controllers. The proposal describes a possiblility that the controllers can avoid the lengthy process of try and correct methods if relatively low set of data is provided to controllers. All the data, those are deemed not fit enough or neverthless would 
not yield a proper result are elimminated and hence never produced at the controller. The creation of the table of the fitness of sensor-data is done offline after innumerous statistical obsevations, thereby creating a lookup table that would be burnt in the non programmable memory. This look up table would be then referred at the time of the running the algorithms for the successful execution of a particular feature. 

The objective of the paper is to finally improve the reliability of the safety critical function of the car. This can be obtained by improving the quality of the data at the sensor level. However an improvement of the quality at the sensor level can at the same time detorirate the overall quality at the functional level. In order to get the best data for a particular function, the quality of the data is defined relative to the function being executed. Hence a two step process is required to finally prove the improvement of the final function based on the obtained local and neighbouring sensor data i.e analysing the fitness landscape of all the sensors.

Right sensor values at the right time has a direct impact on the safety of the vehicles on the roads. Unfortunately, the current computations are done on the wrong sensor values only to discard them at a later stage.

The algorithm provides an offline decision tree through which the CPUs will only be routed those sensor values that will bring some added value to the computation. The CPUs register to the sensors and they are notified whenever there is an update.
The multi sensor fusion does not only takes place in the offline trees itself, but the quality is generally updated during the evaluation of the sensor values at the run time.





















Algorithm


Confusion Matrix and Compromise Matrix.

The successful use of automotive radar sensors in detecting obstacles in adverse weather conditions 
of dense fog has been shown in [?] and [?] and [?] and [?]. Our approach starts with accumulating data from various sensors. This data is then aligned in the temporal and spatial domain. A confusion matrix is build that is specific to the ADAS algorithm and based on the confusion matrix a compromise matrix is built. The job of the compromise matrix is to find the best compromise for that given condition. 

We present a real time algorithm to use data from muliple sensors and use them on the roads. The 
algorithm is divided into two stages. In the first stage, offline priority decision tree is generated and in the second stage online machine learning is done. 
With time, the learning phase takes over the default priority decision tree. Since every car has a different learning period, it also behaves differently. However, the default offline priority decision tree stops it to make any kind of major mistake. 

Generation of a priority tree from the offline data. To be flashed into ROM during the series production.

Learning curves and modification in the priority tree.

Behavioural model is generated that would depict, the relation between the offline tree and the dynamic learning curves. 







Experiments 

The experiments are done on the simulation environment with the help of optical, radar and lidar sensor simulation and the results will be described in detail. 
The paper deals with a theoretical framework of mixing the fitness landscape of data obtained from various sensors. Since there can be a lot of environmental problems, we limit the sample environmental conditions to falling drops of rain at various angles. In our experiments, the choice of the sensors are interesting, because the accuracy of optical sensors suffer from the rain drops whereas the radar sensors do not have any affect from them in detecting any obstacle. As a choice of the ADAS algorithms, we stick ourselves to detection of obstacles on the road. The algorithms are evaluated on a test bench using virtual data in a virtual reality environment. 

As of now, there hasnt been enough research data that could provide an analysis of the fitness of the sensor-data for lane detection algorithms in various einvornmental conditions. Due to the advent of automatic cars the speed of the execution is a determining factor for the success of the automatic driving. The experiments in this paper would be on lane-detection algorithms in various environmental conditions. The experiments would then show the comparison of the time of execution, efficiency of execution between the current algorithms in the car and the proposed algorithm in this paper. 


Other Papers:

Benchmark the performance of the fusion algorithms at the electronic system level using a Hardware in Loop co-simulation. et al Elgharbaway in his paper. All control simulation of the plant is included in the test as mathematical simulation which is called Plant simulation.


Hardware:

Multi Sensor Fusion Chip

Software Architecture: Validation + HW Lopo




====== A paper on method to extract data from sensors ======





======  Various Fusion Frameworks Paper ======




This papers discusses the state of the art of the various frameworks that have been applied to solve the problems of the reliability of the sensor-data in the automotive environment. Additionally it proposes a road map to new methods to improve the efficiency of the overall system. In short, the paper introduces benchmarks, that mathematically confirms the improvement or deterioration of accuracy with which the phenomena is observed and characterised.

Intro:

The first section provides an overview of current frameworks used in the automotive industry. We discuss algorithms such as Bayesian algorithm that had been influential in solving the uncertainities of the sensor-data. We theoretically discuss the multi-sensor architecture that includes the fitness landscapes.

The reliability of the sensor-data has been a key factor in the automation of the automotive features. Nummerous algorithms such as Bayesian, Kalman etc. proposes methods to solve the uncertainities. However, these methods still do not confirm the fitness of the sensor-data even if all the uncertainities has been recorded and applied on these algorithms. This is because, the sensor-data are highly influenced by the environment conditions and communication glitches in Car2Car and Car2X communication. In [1] published in 2000, the authors describe the algorithm of Bayesian programming to counter the above mentioned uncertainities or incomplete knowledge of the sensor data. The paper demonstrates the interest of using probabiblistic reasoning techniques to address the challenging multi-sensor data fusion. In order to avoid false alarms, cut in situations, fragile traffic participants, it is required to solve this problem by improving the existing sensors as well as to fuse the information of different sensor systems with appropriate scene models in order to achieve better accuracy, redundancy, robustness and an increase of the information content. The fusion of multi-sensor data provides not only the statistical advantage gained by combining same source data, but also increases the accuracy with which a phenomena can be observed and characterized. The Bayesian programming addresses the challenge of uncertainities in a variable by relying upon a well established formal theory : probability theory. These uncertain variables if not taken into account while developing the model, can influence the model, so that the execution of the model does not offer the same control as it should have in an ideal situation. Another CARSENSE Project paper [?] presents a software framework for proptyping multi-sensor automotive applications.



======  Offline and online priority graph ======



======  Virtual Reality data extraction ======




New Paper: 
Virtual Reality and Sensors and data extraction from the platfrom
The third section, presents the coupling of the virtual reality platform with the simulated sensors. The section also describes how environmental condtions can be superimposed on the virtual reality platform. In the first section, data is extracted from the simulated sensors in different environmental conditions. Here, different parameters are discussed that are important to get a reliable fitness landscape of the sensors in the corresponding environmental conditions and if deadlines can be met in real time.

Section II presents the coupling of the virtual reality platform with the simulated sensors. The section also describes how environmental condtions can be superimposed on the virtual reality
platform.
In Section III, data is extracted from the simulated sensors in different environmental conditions.
Here, different parameters are discussed that are important to get a reliable fitness landscape of the sensors in the corresponding environmental conditions and if deadlines can be met in real time.  




