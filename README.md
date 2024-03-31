- ## If MainModule already exit SubModule2 (This workaround not keep the history of SubModule2)
	```
	├── MainModule
	│   ├── SubModule1
	│   └── SubModule2 ---------> need to seprate this module to other repo
	```

	- ### Create new SubModule2 repo on GitHub, and get the URL: 
	  	```
		https://github.com/TrdHuy/SubModule2_T1.git
	   	```
	- ### At SubModule2 folder, run:
		 ```
		git init
		git add .
		git commit -m "init repo"
		git remote add origin https://github.com/TrdHuy/SubModule2_T1.git
		git push -u origin master
		 ```
  	- ### At MainModule folder, run:
		 ```
		git rm -r SubModule2 --cache
		git submodule add https://github.com/TrdHuy/SubModule2_T1.git SubModule2
	  	git commit -m "convert to sub2 repo"
	  	git push origin master
		 ```


- ## If MainModule already exit SubModule3 (This workaround will keep the history of SubModule3)
	```
	├── MainModule
	│   ├── SubModule1
	│   └── SubModule2 
 	│   └── SubModule3 ---------> need to seprate this module to other repo	
	```

	- ### Create new SubModule3 repo on GitHub, and get the URL: 
	  	```
		https://github.com/TrdHuy/SubModule3_T1.git
	   	```
	- ### At MainModule folder, run:
		 ```
		git filter-repo --path SubModule3/ --to-subdirectory-filter SubModule3 --force
		git remote add origin https://github.com/TrdHuy/SubModule3_T1.git
		git push -u origin master
		 ```
