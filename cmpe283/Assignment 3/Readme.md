# Assignment 3

Pre-requisites - Setup for Assignment 1 should be completed

Requirements:

For CPUID leaf node %eax= 0x4FFFFFFD: Return the number of exits for the exit number provided (on input) in %ecx. The output should be returned in %eax.
For CPUID leaf node %eax= 0x4FFFFFFC: Return the time taken to process the exit number provided (on input) in %ecx. Return the higher 32 bits of the total time taken to process all exits in %ebx Return the lower 32 bits of the total time taken to process all exits in %ecx
Steps:

1. Add code to KVM at file /linux/arch/x86/kvm/vmx/vmx.c and /linux/arch/x86/kvm/cpuid.c

2. Modify cpuid.c and vmx.c to implement the above functionality.

3. Build the code sudo make modules sudo make modules_install sudo make install reboot

4. Open virt-manager and start virtual machine.

5. Install CPUID package inside the inner vm. sudo apt-get install cupid

6. For cpuid 0x4FFFFFFC

7. Execute dmesg command to view all the exits available count.

<img width="728" alt="166089541-32df8459-5aa6-4f27-9232-acdbeda55989" src="https://user-images.githubusercontent.com/71619460/166091964-4c4720e1-5f3c-45bd-89dd-2e2179091eea.png">

8. Comment of the frequency axis Frequency of the time spent depends on the type of exit.The number of exits tends to increase if more privileged operations are performed by the system
<img width="472" alt="166089576-8f6f7eaf-28dd-482f-8760-6a28bba9cde0" src="https://user-images.githubusercontent.com/71619460/166091998-be57b377-9095-484b-ab25-7f0aeff315b9.png">
9. Which are the most frequent and less frequent exit types? Most frquent - MSR_WRITE -Cycle count 4859559731 Less frequent - DR_ACCESS - Cycle count 7625
<img width="472" alt="166089585-ebab3856-75c2-4ddd-a43d-deb25139244e" src="https://user-images.githubusercontent.com/71619460/166092025-908a9c49-ec7a-42aa-928a-7816571000e2.png">
10. For cpuid 0x4FFFFFFD
11. Execute dmesg command in the host system’s terminal to count the exits available
<img width="370" alt="166089658-052172d3-8649-4a8e-bd94-c9fdc045602b" src="https://user-images.githubusercontent.com/71619460/166092041-4bf658a2-6682-4b9f-aa5e-beec6ff24c99.png">
12. Cpuid - I 0X4fffffffd -444 - output for invalid exit code
<img width="440" alt="166089665-f7830bec-f0f1-4357-b4c0-576df3940690" src="https://user-images.githubusercontent.com/71619460/166092062-878ce032-67a4-4d3d-ba84-e5a2551f062a.png">
14. Comment of the frequency of exits Answer: Frequency of the exits depends on the system use.The number of exit increases as more priveleged operations are performed.
![166089756-3ce2d277-244a-443d-ae8c-cf6cf27da0dc](https://user-images.githubusercontent.com/71619460/166092100-667a18fe-5593-47d3-b991-7c8558c55ab2.png)
15. Of the exit types defined in the SDM, which are the most frequent? Least? Most frequent exit - MSR_WRITE(count -605825) Least frequent exit - DR_ACCESS(count-8)
![166089772-71989864-dec4-40c1-82d2-a8045772e415](https://user-images.githubusercontent.com/71619460/166092142-1dc3f359-e775-4c41-a5d1-eebba8c59fea.png)


