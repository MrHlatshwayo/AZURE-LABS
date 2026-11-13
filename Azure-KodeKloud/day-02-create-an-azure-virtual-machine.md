# Day 2: Create an Azure Virtual Machine

- **Status:** Complete
- **Track:** 50 days of Azure

## Objectives
- What Azure concept or service was covered?
 This Labs tests my ability to provision and configure Virtual machine in Azure according to the requirements.

- What problem was this lab intended to solve?
  The Nautilus DevOps team is planning to migrate a portion of their infrastructure to the Azure cloud incrementally. As part of this migration, you are tasked with creating an Azure Virtual Machine (VM).
## Azure Resources
Record resource groups, regions, subscriptions, and resources used here.
  The requirements are:
1) Use the existing resource group.
2) The VM name must be `xfusion-vm`, it should be in `centralus` region.
3) Use the `Ubuntu 24.04 LTS` image for the VM.
4) The VM size must be `Standard_B1s`.
5) Attach a default Network Security Group (NSG) that allows inbound SSH (port 22).
6) Attach a 30 GB storage disk of type `Standard HDD`.
7) The rest of the configurations should remain as default.

## Commands and Configuration
```bash
#I logged into the Azure portal usig the email provided by the lab and temporary acess token
#From there I went to virtual machine page on the azure portal and clixcked the create button
#Once I was now in the Virtual Machine creation page, I configured the virtual machine according to the specifications provided by the lab.
#Once configured I set out to create the VM but came across an error when trying to download and generate the resource with ssh key pair.
#So I went to the ssh keys page on the azure portal and created a new ssh key pair and downloaded the private key.
#From there I went to the virtual machine creation page and configured the ssh key pair option to use an existing key pair and chose the recently created one now linked to my resource group.
#Once configured I could now create the resource and wait for deployement to finish
#Back on the lab terminal i had to veirfy first that ssh directory exists using the following command.
cd ~/.ssh
#Once I saw no erro showed up I was able to start create the key file named azure_vm_key using the following command:
cat << 'EOF' > ~/.ssh/azure_vm_key
-----BEGIN RSA PRIVATE KEY-----
MIIG5AIBAAKCAYEAvVzdiyt3h80A7ONbxPOnSjFnR4aKGrWyOeSQBSU7MKiUgfiz
yMevl68vk9w+99SGIrBqC8aTZrynDxmNt82mbixrHn8tdzi7inud79fzIHkaEu/8
DIIDF0D/Fi2JD7SRvzIQ5y3pGUPgBm320LqaNwIM4BOGKpnM9CeKjr/5DACzqXPp
JFEJXk/qwib+vt0FH0z3ap8inN2ZMq9ModSf8wAcW32EDm/BLTDWxddilEVyZHhL
rV/1gpTJUUg/2QEt+saxxJ45liktvvrMKow+/UilZth//qRfX3Ko6g+4fsn7f3Sm
J/M6WUknOa1YxUL2N9xHMVC3f0QpU5XQExOvHJdyotAks8fd8feYbFLuKVswFvsV
PtwNWeSF9a4Wtv9pPIWNmCuMGaoxAkTNuZqriRIkguywdm6O0UYPzPdLSGpKyxRw
jDtALJcMRbBi7q975qiOnUTscZr9UegA4cwk/NaWDEcWrDbUvuQBQ8wl0vSk4Ywy
YeC8bava8wuKTrgxAgMBAAECggGAZrE3ACM5dm8Jom4GNYABaC30mYhv2t5QYi7+
n5u6RsAVkYqjTS5lnngF8ETP7SzW9XcAe5RcGaoTWw/7mAMxz6vNB8PmjzI4GnjB
hPFyy1iBeGWnJc1YCcNY0tks7FR7edmX6xctw2LY2gPGhxm7SjuVaeuMpgu0Z3AO
Jy4azJSQ2kOe2vALiZcDc/kby7wm6/ucbbkRV0qhqygAAf9CItEbj8440G9wrqY+
wxn0Pv6Oc8f9Gm/gv8kaiDcLUQ7exZQhXHPjQwySuJIr2VTW/SwrEijv/rmXdPAr
Y9Kbsd6hrHup+F7kRLlMmvs4N7JUGUC35MTSnUloufHXxSi/m7cBbCxEi0wUiB4V
AexmbNzXZDlTxAuhTcDbx5Y6EL5fmZw/ZGxdrYAgtsQvC/tcVZbS8gnY5ODFDHdZ
LQYt6BuZoxeOU+ocw/9A/gCipExxaR0mj9aMi9eV7IZ/nLcSws0DyKdEHbRMk/kg
ce/GJJlpeU9dp7v4VTKlY8EmuycFAoHBAPM5o5FEPXIbx37UC+heo7GA1gOk/KPt
5+4RJtyYAvV6qLOMKM+FdsBgmAj9YzZnW7e1P3RoK1b5BCz5NSdPr/6twm7tC0Ca
bPFzEHqkyOyKICAupkzWO/iUzOly12fznsW+bhjenKXrqWzTIenyWD56MdUgkVKG
o/RoDRK1APt2nc+JOrRiQMJgpSO9tXQeFWVE0atz9ju0JI6JQCtJ4P3j/vrLBRAW
oKgWeO5/mwqbw8yR5548eiRuIfBPr928kwKBwQDHTwCj9BKMtl4q9+Dercm55A7t
90nDEnJpUs/HmVmyARERm9F0OdcxLLftlCeGhvwYq0SipgLW76GuGFi/WTbqLUXH
H/Ozz/DwesF3fmMsgANQsYJC0pLXY2A3wkEyN3lqoKbt8l84o2UCp+dKuzsW/2hC
xS2xM45eNS0V3uWx55zUHuOs/KeU0zQ0tt3u+WYP4amPwSfdZ8YkisTeE7CRHIku
85ifRT8HRKqTV/cl9bzAlPfqScSOswS7fiRidqsCgcBrn3qQAdkKj94zcZKfTJk0
JuUMEco0o0W4IuDGRYExrAfQAtngEZddQqCjgbOP1CZSYKHmWV2sC13cpJzveyRO
Fgbt3HfZKzu/jwGgsx+xAuF6PAob/8Pjl7wgJE/KUJNVvpCq8n3wMRnz7GyaP0Dq
zFkWjGWhVbBgqlX2jB8WJgNoXLmcLcmn+Om5qe0Lp3AiMlRwgExZWLnAVF0Pio5C
6creoEzqNIj8N41lQxOQmyIFeB4791i4m/7qfeg8vn8CgcEAqt1XtzbvECLn5/5J
-----END RSA PRIVATE KEY-----5ovA5nfNk9CSQEHGvWU9nMhyQ==Kfdw98S9
> 
EOF
#After this I went one to verify that it was successful using the following command:
cat azure_vm_key
#This ouputed the contents i added and i could now ssh to the resoucre
#Now I intially used the follwoing command to ssh to the resource:
ssh -i ~/.ssh/azure-vm_key azureuser@(my resource ip)
#this command worked and i was prompted to confirm if i wanted to connect to the host and i typed yes
#now to my surpise it brought forth a error being my permissions were too open, so i limited them using the following command:
chmod 600 azure_vm_key
#this limited it to only me having the ability to read and write the file.
#from there i retried the ssh command and it was a success, allowing me to complete the lab
```

## Validation Evidence
Record screenshots, command output, portal checks, or other evidence here.
![](Pasted%20image%2020261113123637.png)
![](Pasted%20image%2020261113124432.png)
![](Pasted%20image%2020261113124523.png)
![](Pasted%20image%2020261113124609.png)
![](Pasted%20image%2020261113125045.png)

## Results
Record what was completed and any issues encountered.
![](Pasted%20image%2020261113125317.png)
![](Pasted%20image%2020261113125725.png)
![](Pasted%20image%2020261113125827.png)
![](Pasted%20image%2020261113130001.png)
![](Pasted%20image%2020261113130210.png)

![](Screenshot%202026-11-13%20132811.png)
## Notes
Record lessons learned, cleanup steps, and follow-up work.
What I learned in this lab was the familiarity between Linux and bash in the CLI. I also learned the importance of permissions , more especially least privlege being the standard when interacting with the cloud.