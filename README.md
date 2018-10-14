# SSH Root Login Email Alerts

Simple bash script to keep track of what is happening with servers and who logs into server as root.

This script shows a simple way to know when someone logged in as root and it send an email alert notification to the specified email address along with the IP address of last login.

## Note
Add this script to the .bashrc file in the root directory.


output=$(last|grep root)

test_exit_code=$?

  if [ "$test_exit_code" == 0  ]; then
  
    echo "ALERT - Root Shell Access on $(hostname | awk '{print toupper($0)}'):' `date` `who|grep -m1  root`" | mail -s "Alert:     Root Access from  $(last |grep niko | awk '{print $3;exit}')"  email@yourdomain.com
    
  fi
