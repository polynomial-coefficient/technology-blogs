**无声版**

# STEP 1

```

# PART 0
touch extra.sh;  


# PART 1

ls >> copy2folder.sh;  

sed -i 's/^/cp extra.sh /g' copy2folder.sh;  
sed -i 's/$/\/;/g' copy2folder.sh;  


# PART 2

ls >> handleExtraScript.sh;  

sed -i 's/^/bash /g' handleExtraScript.sh;  
sed -i 's/$/\/extra.sh;/g' handleExtraScript.sh;  


```

<hr>


# STEP 2

**复制下方至 extra.sh**

<BR>

``````
station_dir='/home/user/BeforeHandler/mine/';
echo 'station_dir:';
echo $station_dir;
echo -e '\n';

execute_path=$(cd `dirname $0`;pwd);
echo 'execute_path:';
echo $execute_path;
echo -e '\n';

m4s_video_name=`find $execute_path -iname '*video.m4s*'`;
# substring
echo 'm4s_video_name:';
echo $m4s_video_name;
echo -e '\n';

json_name=`find $execute_path -iname '*entry.json*'`;
echo 'json_name:';
echo $json_name;
echo -e '\n';


# get from json file
avid_var=`cat $json_name | grep -oP '(?<="avid":)(.*?)(?=,)';`
echo 'avid_var:';
echo $avid_var;
echo -e '\n';

title_var=`cat $json_name | grep -oP '(?<="title":")(.*?)(?=",)';`
echo 'title_var:';
echo $title_var;
echo -e '\n';

# replace '/'
new_title=${title_var//\//};
# replace '\'
new_title=${new_title//\\/};

new_title=${new_title//\】/};
new_title=${new_title//\【/};
new_title=${new_title//，/};
new_title=${new_title// /};
new_title=${new_title//|/};
new_title=${new_title//！/};
new_title=${new_title//。/};
new_title=${new_title//，/};

new_title=${new_title//\(/};
new_title=${new_title//\)/};

new_title=${new_title//『/};
new_title=${new_title//』/};
 
new_title=${new_title//「/};
new_title=${new_title//」/};

new_title=${new_title//_/};

new_title=${new_title//《/};
new_title=${new_title//》/};

new_title=${new_title//、/};
new_title=${new_title//\~/};
new_title=${new_title//？/};
new_title=${new_title//：/};

new_title=${new_title//\）/};
new_title=${new_title//\（/};

new_title=${new_title//@/};
new_title=${new_title//［/};
new_title=${new_title//］/};
new_title=${new_title//\#/};


echo 'new_title:';
echo $new_title;
echo -e '\n';


# move
new_file_name=$station_dir$avid_var-$new_title.mp4;
echo 'new_file_name:';
echo $new_file_name;
echo -e '\n';

mv $m4s_video_name $new_file_name;



``````
