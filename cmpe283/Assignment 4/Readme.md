# ASSIGNMENT 4

## Questions
## 1. For each member in your team, provide 1 paragraph detailing what parts of the lab that member implemented / researched.
I did the assignment on my own
Steps to follow:
  * Verified that Assignment III code is functional.
  * Ran assignment 3 code and took output for Nested paging 
  * Tested and verified the results
  * Documented the steps and results
  * Switched KVM to shadow paging (ept=0)
  * Ran assignment 3 code and took output for Shadow Paging 
  * Tested and verified the results
  * Documented the steps and results
  
## 2. Include a sample of your print of exit count output from dmesg from “with ept” and “without ept”.

## STEP 1:
  * Open virt-manager and start virtual machine. Run case 3 from previous assignment (To print all exit type wise counts). 

  * Execute dmesg for nested paging (i.e., with ept)
  
  ![ass_1_1](https://user-images.githubusercontent.com/15766915/166091694-4ee379b8-7acb-4710-9926-c6ff1e367ca2.png)

  
## STEP 2: 	

 * Execute following commands to switch from nested paging to shadow paging:  
	
   *	sudo rmmod kvm_intel && sudo rmmod kvm && sudo modprobe kvm && sudo modprobe kvm_intel ept=0
   *	Reboot
 
 * Execute dmesg for shadow paging (i.e., without ept)
 
 ![ass_4_2](https://user-images.githubusercontent.com/15766915/166091699-c5bb9a6c-1a66-44a2-8d61-5a413de11343.png)


## 3. What did you learn from the count of exits? Was the count what you expected? If not, why not?

- In the case of shadow paging, we can observe from the output, maximum exit occurred of type “CR_ACCESS ".
- Also, INVLPG exit is present in case of shadow paging. INVLPG exit is used by hypervisor to invalidate translation in the TLB.

## 4. What changed between the two runs (ept vs non-ept)

Nested Paging (ept=1)             |  Shadow Paging (ept=0)
----------------------------------| ---------------------------------
The VM exits for “EPT_VIOLATION”  | The VM exits for “INVALPG”
The VM exits for “EPT_MISCONFIG”  | Count of exits for reason “CR_ACCESS” increased significantly. Exit count seen for “XSETBV”
                                  
* In case of shadow paging the count of exits for reason “CR_ACCESS” increased significantly as hypervisor takes exits on access of CR register


<img width="836" alt="ass_4_3" src="https://user-images.githubusercontent.com/15766915/166091701-1808fb56-ffd6-41ba-8869-beddc71e1a52.png">



