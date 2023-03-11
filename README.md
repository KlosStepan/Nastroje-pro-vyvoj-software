# Nastroje-pro-vyvoj-software
I chose these 6 tasks to be solved // TODO 1 more + 1 extra Kubernetes
## 02-Git - S1 Version control systems(Git, SVN, Hg)
This assignment is completed from previous year so it's just copy-pasted from back then. Solution is called **reseni.txt**. 
## 03-Make - S2 (Make, Ant, MS Build)
Solved this year, there are 2 Makefiles (one **root folder**, second **mydb/src**) that are working together with all requirements met.  
## 05-Build/CMake
CMakeLists.txt root, and project folder. 
## 08-Testing/JUnit - S3 Functional testing(JUnit, NUnit)
Testing was tried on Java/JUnit and result are in separate public repo along w/ code and additional information: [KlosStepan/UnitTesting-JUnit](https://github.com/KlosStepan/UnitTesting-JUnit).
## 09-Doxygen
Last assignment that was chosen was automatic generation of documentation. It's for my custom project [KlosStepan/SwimmPair-Www](https://github.com/KlosStepan/SwimmPair-Www) in PHP, so it's a bit different from what we've talked about on the lesson, however, all requirements were met as well. The documentation is running in my K8s Cluster on address [docu.swimmpair.cz](http://docu.swimmpair.cz).
## 10-perf S4 Performance analysis (GProf, JVisualVM)
Lalala not yet done.  
## 00-Kubernetes/Docker
I set up my DOKS-Kubernetes and migrated several LAMP applications over there. I worked with multiple nodes, chose appropriate images for situations and set up my own database with persistent volume.  

# Tasks feedbacks
## 02-Git
Good tool, but I was confused by the lecture and tasks in the second half of assignment. I use Git on regular basis but with different set of tasks at job/for my stuff.
## 03-Make
Very good task, but bit overwhelming assignment in regards to number of files (and linking agains libraries). I wasn't sure whether I should wildcards the .h/.c couples so I just wrote them straight away.
## 05-Build/CMake 
Almost logically copypasted prev. task, but CMake is more useful than Make from my point of view, since it's abstraction above Make, MSBuild etc.   
## 08-Testing/JUnit
Great task - JUnit is very intuitive and everybody knows Java so the little coding we had to do was fun. 
## 09-Doxygen
Probably the best task - I would encourage students to use this for documenting of their zapoctaks or bakalarkas. It took me some time to make it working with PHP, since it's not primary language for Doxygen but I installed PHP by DEVSENSE for VS Code which helped me with automatic annotations and finished it successfully. Also, the tasks very very good to see non-default options that are, in fact, the best that Doxygen provides.   
## 10-Performance/GProof
Idk yet

## Would be appreciated by me
- npm/js ecosystem
- Docker, Kubernetes or Dockerfile for local development
- cloud monitoring/cicd - Prometheus, Github Actions / leveraging Kubernetes container instantiations for automatic testing 