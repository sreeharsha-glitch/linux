Open cpuid file in /linux/arch/x86/kvm folder.
Add code for the below functionalities

1. For CPUID leaf node %eax=0x4FFFFFFF:
   Return the total number of exits (all types) in %eax
2. For CPUID leaf node %eax=0x4FFFFFFE:
   Return the high 32 bits of the total time spent processing all exits in %ebx
   Return the low 32 bits of the total time spent processing all exits in %ecx
   Open vmx.c file in /linux/arch/x86/kvm/vmx folder.
   Modify this file accordingly to handle the above functionalities
   Rebuild the kernel using make -j 1 modules M=arch/x86/kvm command
   Perform loading and unloading of kvm kernel module (kvm.ko) and kvm-intel-module (kvm-intel.ko) using the following commands:
   sudo rmmod arch/x86/kvm/kvm-intel.ko
   sudo rmmod arch/x86/kvm/kvm.ko
   sudo insmod arch/x86/kvm/kvm.ko
   sudo insmod arch/x86/kvm/kvm-intel.ko

To test the functionality
Run sudo apt update command
Run sudo apt-get install cpuid command
Create test codes for all the functionalities in the inner with file name test_assignment2.c
Install gcc and compile the code using gcc test_Assignment2.c
Run this test file with ./a.out
