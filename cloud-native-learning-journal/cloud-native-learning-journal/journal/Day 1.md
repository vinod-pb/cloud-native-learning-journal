
# 📅 Day 1 — Kickoff


## ✅ Linux Practice
- Commands tried:
  - `pwd` → shows current directory
  - `cd` → move between folders
  - `ls -l` → list files with details
  - `mkdir` → create new folder
  - `touch` → create file
  - `echo "text" >> file` → write to file
  - `cat file` → read file
  - `chmod` → change permissions
- Example:
-
	`mkdir day1-practice`
     `cd day1-practice`
     `touch notes.txt`
    `echo "My first Linux note" >> notes.txt`
  `    cat notes.txt`
  
## [[Cloud-Native Notes:]]

 - Cloud native = building apps that are scalable , resilient , portable
 - Containers -> package the application and its dependencies runs anywhere
 - Microservices -> small services that scale independently 
 - Service mesh -> control communication between the services
 - Infra immutability -> don't edit the servers rebuild
 - Declarative API -> describe what you want?

**Reflection:** Containers are the base layer — without them, microservices and service meshes wouldn’t work.

 ## [[12 Factor]] 

- Config -> Keep in the environment not in the code.
- Process -> The app  should be stateless and no local memory. 
- Dependencies -> Explicitly list out the  library dependences   
- Code base -> one code based tracked deployed many


**Reflection:** The 12-Factor principles are habits that make cloud-native apps easier to build, scale, and manage.
-