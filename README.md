# Machine-Learning-Operations-mlops

AI: It is the wider domain, adding intelligence to the machine, will not get inference from patterns like if-else, it  learns from its intelligence. Different domains in AI
ML: using a specific algorithm, and training it on data, the machine learns from data and performs intelligently, algos are like logistic regression, and linear regression.
DL: within ML when we use neural network tech then in that sense we call it deep learning, we use it in image recognition and speech recognition
LLM: In further smaller domains there comes LLM like chat gpt.

mlops merges ML + Dev Ops + Data engineering

What is DevOps, the story behind it?

software development life cycle(sdlc) involves an idea, requirements gathering, planning, designing, development, testing, production (deployment), and maintenance.

A person comes in and wants to build software and our product manager asked we have two methods 1. waterfall and 2. agile method. In waterfall, we take requirements, designing, develop all the stuff, and in the end, we got came to know the requirements were not satisfied/went wrong. In agile give requirements one by one build it and see the results, build as you go. The person chose the agile method. (Before devops there were two parts one development and operations part). By getting one requirement from the person the development team did the development(code) of the feature after performing the unit testing handed over to the operations team so that they deploy on the server(performs server-side testing after deployment, billing plan(what server to use, cost, which resources(VMs) to use, making accessible publically, server configurations)) the developed feature. The operations team do not have/know configuration of the software as the developers had/did due to that they see software fail when testing it as they do not have the configurations. Then the operations team get back to dev team asked them software is not working , dev team tell them these requirements need to use, and then op team update the software. The time is consuming more on the operations team side because they follow waterfall process called ITIL/ITSM, on opeartions side agile method is not used, they have to follow the process in a flow, a standard. In that time dev team gave another feature but op team is stuck in first feature still, Due to this product deliverable went late the person's task not completed, (person and product manager are in worry), to overcome this situation they hire the deveops engineer.  Devops engineer came and did a lot of things automated.  

In summary Dev is agile means regular and quick changes done, In ops they follow ITIL in which waterfall model or process is followed.
At high level how automation done in devops/ Main automation parts in devops: code build (the code we have builded/commited), code testing(unit), software testing, infra changes(configurations , vms, plans etc), deployment.

Now in detail What is happening in Devops/ how automation done behind the scene: Git repo where our project is placed(commit) -->> jankins->> build file ->> artifactory (Jfrog)--> in dev tree ->> Q/A team (testing, triggers the build)-- > build in release --> deploy on servers

 CI/CD stands for continuous integration/continuous deployment or delivery. First comes version control system (GIT). Git provides collaboration means multiple persons can work on different feactures of same project at same time through branches, on git we can share working code while working and fixing any bugs. Second comes the ci/cd pipeline software for example jankins. When a collaborator does a commit it goes to the jankins where our first bulid will created, when creating build different actions are performed 1. package managers (gradle, maven, make) it manages all the libraries/packages required to run application. Manitaining the libraries, making in package form is all done at jakins automatically. 2.Performs the unit testing, we had test file containing test case uploaded in git repo, test file can be created automatically as well, this test file excuted at jankins automatically, if test passed successfully it generates the build file, the build file goes to the artifactory(contains packages, build the images of those packages and deploy image). (Artifactor has different trees one dev tree second release tree.) Build file placed in dev tree of artifactory, which means here this build is to go for quality assurance (Q/A) team that they can test my code(from here q/a part think of like operations part), they run that build onto servers/deploy it there on servers, performs there three types of testing 1. functional testing: testing by integrating this feature with other components/app, 2. low testing 3. performance testing. When q/a confirms everything is ok then they trigger the build and build goes into the release tree of the artifactory. When build goes in release branch then we call it as continuous delivery(means this build/feature is good to go in production, it is delivered not deployed yet). Then picking up package/software/module from artifactory release tree when it is deployed in live containers so that it is used publically we deploy in canary environment means we allow some traffic on new module not all or in broad envronment. When we put our release part in canary or broad environment then that part is called continuous deployment. This all ci/cd process is done automated.
Steps of devops or ci/cd pipeline:
1. Developer commit
2. Code Build artifact(will go in build artifactory in the form of jar, var, tar or any)
3. Code testing (unit testing) done as part of step 2
4. Code analysis vulnerabilities analysis
5. Deploy changes to staging
6. DB/config changes
7. QA testing
8. Deploy to product (first in canary)
9. Go live (continuous delivery) 
