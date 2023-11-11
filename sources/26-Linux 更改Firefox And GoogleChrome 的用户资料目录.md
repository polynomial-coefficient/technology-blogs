

# bashrc

```

alias firefox="bash /home/mybasic/firefox-previous-load.sh"
alias google-chrome="bash /home/mybasic/google.chrome-previous-load.sh"

```

<hr>

# Chrome

```

partition="/dev/sda6";
dir_name="/media/memory";

if mount | grep -q "$partition on $dir_name"; then 
 	echo "业已Mount";
 	google-chrome --user-data-dir=$dir_name/Program-Files/browser-temporaries/GoogleChrome/LinuxUserData/Default;
else 
	echo "尚未Mount, please: sudo mount /dev/sda6 "$dir_name; 
fi

```

<hr>

# Firefox

```
partition="/dev/sda6";
dir_name="/media/memory";

if mount | grep -q "$partition on $dir_name"; then 
 	echo "业已Mount";
 	firefox;
else 
	echo "尚未Mount, please: sudo mount /dev/sda6 "$dir_name; 
fi

```
