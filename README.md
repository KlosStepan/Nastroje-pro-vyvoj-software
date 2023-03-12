# Nastroje-pro-vyvoj-software
I chose these 5 tasks to be solved + I would like to substitute Kubernetes/ migration for Task 10. It couldn't be solved on Mac due to lack of `gprof` port, however, Monitoring/Performance is concerned in my substitute "report/essay", more below.  

I spent decent half of year exploring several Kubernetes production options (Amazon AWS/self-hosting of plain K8s,  OpenShift distribution/ **ended up w/ managed DigitalOcean Kubernetes**). Task 10 is focused on monitoring and Prometheus and Elastic Search was mentioned in the lectures. I will soon (in next 3 months) be continuing with exactly this, I have no practical knowledge but only theoreticaly read about it. Cluster setup description is in folder /100-DOKS-Kubernetes w/ nested README.md.  

(I would appreciate input about these topis - Prometheus, Elastic search, Zabbix and Redis, or best practices for logging and monitoring of Kubernetes Cluser (and its nodes) I would more than gladly accepted it - I'm currently exploring options and stuff - I have not deployed anything into it yet.)

# Tasks overview

## 02-Git, S1 Version control systems(Git, SVN, Hg)
This assignment is completed from previous year so it's just copy-pasted from back then. Solution is called **reseni.txt**. 
## 03-Make, S2 (Make, Ant, MS Build)
Solved this year, there are 2 Makefiles (one **root folder**, second **mydb/src**) that are working together with all requirements met. Nested targets are called via main one.    

Calling `make` or w/ targets in folder **zadani** works. 

    zadani
    ├── Makefile # Root folder Makefile - proxy
    └── mydb
       └── src           
          ├── *.h/*.c  # All proj. files
          └── Makefile # Nested Makefile - logic
Tricky thing are dependencies: when one of the required items by the output object is changed (or touch-ed) the object `data.o` is recompiled and stuff that needs it is recompiled as well. Otherwise when there are no changes and we `make` project unchanged items are still during the build process and are reused.  
```makefile
data.o: data.c data.h textfileio.h linklist.h	
	$(CC) -c $(CFLAGS) data.c
```  
## 05-Build/CMake
Same structure, but filed called CMakeLists.txt. CMakeLists.txt in **05-build**, CMakeLists.txt in **05-build/mydb/src**. The upper CMakeLists.txt in `zadani` is much simpler than his predecesor's (Makefile) equivalent.
```CMake
cmake_minimum_required(VERSION 3.0)
project(mydb)
add_subdirectory("mydb/src")
```

In folder 05-build we can invoke **all**, targets **testserver** / **testclient** / **testadmin** and non-outpu **clean-all** which delets stuff.
```zsh
05-build> cmake --build .
05-build> cmake --build . --target testserver
05-build> cmake --build . --target clean-all
```
Stuff is getting built in the nested folder, let's briefly look at what happens.
```zsh
➜  05-build git:(main) ✗ pwd
/Users/stepo/Documents/Nastroje/22/05-build
➜  05-build git:(main) ✗ cmake --build .
[  3%] Linking C static library libmydb.a
[ 77%] Built target mydb
[ 81%] Linking C executable testclient
[ 85%] Built target testclient
[ 88%] Linking C executable testserver
[ 92%] Built target testserver
[ 96%] Linking C executable testadmin
[100%] Built target testadmin
➜  05-build git:(main) ✗ cmake --build . --target clean-all
Built target clean-all
```

## 08-Testing/JUnit, S3 Functional testing(JUnit, NUnit)
Testing was tried on Java/JUnit and result are in separate public repo along w/ code and additional information: [KlosStepan/UnitTesting-JUnit](https://github.com/KlosStepan/UnitTesting-JUnit).
## 09-Doxygen
I chose assignment for automatic generation of documentation. It's for my custom project [KlosStepan/SwimmPair-Www](https://github.com/KlosStepan/SwimmPair-Www) in PHP, so it's a bit different from what we've talked about on the lesson, however, all requirements from the list were met. The HTML output documentation is running in my K8s Cluster on address [docu.swimmpair.cz](http://docu.swimmpair.cz). There is nothing to say except just changing flags and preparing tens-hundreds of annotations and thinking about captions hmpf. But the result was definitely worth it. 
## ~~10-perf S4 Performance analysis (GProf, JVisualVM)~~
XX gprof not working on Mac. I wanted to do profiling and analysis, but `gprof` is for Mac (AFAIK). 

I did some simple monitoring and benchmarking in PHP [SwimmPair-Www/dummy_data_benchmark](https://github.com/KlosStepan/SwimmPair-Www/blob/master/dummy_data_benchmark.php) which I recorded for testing purposes in Cluster [benchmarks/doks-ams3/outputs](https://github.com/KlosStepan/SwimmPair-Www/tree/master/_misc/doks-ams3) and on my computer [benchmarks/mbp2018-i5-8259U-16-512/outputs](https://github.com/KlosStepan/SwimmPair-Www/tree/master/_misc/mbp2018-i5-8259U-16-512) for comparison.   

I will, however, use Prometheus soon for cluster monitoring in my Kubernetes cluster. I partially set it (next chapter). 
## 100-Kubernetes/Docker
I set up my own DOKS Kubernetes at [digitalocean.com](https://www.digitalocean.com) and migrated several LAMP applications over there. I work with multiple Node setup, chose appropriate images for different application situations and set up my own database with persistent volume.  

I have repository about it, but I don't feel confident opening it for the public yet. I will just copy-paste it to folder of this repository w/o some "confidential stuff", which might reveal structure or ports in my cluster.

# Tasks feedbacks
## 02-Git hw_score: 5/10
Good tool, but I was confused by the lecture and tasks in the second half of assignment. I use Git on regular basis but with different set of tasks at job/for my stuff.  
## 03-Make hw_score: 6.5/10
Very good task, but bit overwhelming assignment in regards to description and number of files (and linking agains libraries). Otherwise I would give 8/10. I wasn't sure whether I should wildcards the .h/.c couples so I just wrote them straight away. It took me longer to orient myself in the structure of project. I also had problem with linking of `-lhistory` on Mac.
## 05-Build/CMake hw_score: 7/10
Almost logically copypasted prev. task, but CMake is more useful than Make from my point of view.  
**CMake** is a wonderful tool which serves as an API language for either Makefile, MSBuild etc. It reminds me of advent of jQuery which unified DOM operations across different browsers.  
## 08-Testing/JUnit hw_score: 9/10
Great task - JUnit is very intuitive and everybody knows Java so the little coding we had to do was fun. Very demonstrative, good work/knowledge ROI on this homework.
## 09-Doxygen hw_score: 10/10
Probably the best task - I would encourage other mates to use this for documenting of their zapoctaks or bakalarkas. It took me some(read more) time to make it working with PHP, since it's not primary language for Doxygen but I installed PHP by DEVSENSE for VS Code which helped me with automatic annotations and finished it successfully. Also, the tasks very very good to see non-default options that are, in fact, the best that Doxygen provides.   
## 10-Performance/GProof
not working on Mac :/ I would appreciate cloud related equivalent stuff.
___
## Wishlist of items what I think might be interesting for somebody (me included)
- npm/JS ecosystem (maybe bundling)
- testing of PHP backends, web applications, Cypress
- Docker, Kubernetes for web production in cloud
- using Docker for local development w/o installation of different runtimes (runtime inside the container & **volumes: - ./:/var/www/html** )
- cloud monitoring, ci/cd - Prometheus, Github Actions, CircleCi / leveraging Kubernetes container instantiations for automatic testing, setting up test pre-production namespaces for running tests before deployment