**有声版**


# step 1

```

# part 0

touch fabricate.sh;

# part1

find . -iname "*video*m4s*" >> copy2dir.sh;

sed -i 's/^/cp fabricate.sh /g' copy2dir.sh;  
sed -i 's/video.m4s/;/g' copy2dir.sh;

# part2

find ./ -iname "*video*m4s*" >> executeDirScript.sh;

sed -i 's/^/bash /g' executeDirScript.sh; 
sed -i 's/video.m4s/fabricate.sh;/g' executeDirScript.sh;

```

<hr>


# step 2

**复制下方至 fabricate.sh**

<br>

```
# 获取实际路径
execute_path=$(cd `dirname $0`;pwd);
echo $execute_path;

# JSON 数据
json_data=$(cat $execute_path/../entry.json);
echo $json_data;

# 使用正则表达式和 sed 提取 "avid"、"title" 和 "page" 节点的值
avid=$(echo "$json_data" | grep -oP '(?<="avid":)(.*?)(?=,)');
echo "avid: $avid";
title=$(echo "$json_data" | grep -oP '(?<="title":)(.*?)(?=,)');
echo "title: $title";
page=$(echo "$json_data" | grep -oP '(?<="page":)(.*?)(?=,)');
echo "page: $page";

# 提取的值
abstract_val=$(echo "$avid-$title-$page");
echo "abstract_val: $abstract_val";

# 替换字符
output_file_name=${abstract_val//：/};

output_file_name=${output_file_name// /}
output_file_name=${output_file_name//。/}
output_file_name=${output_file_name//，/}
output_file_name=${output_file_name//！/}
output_file_name=${output_file_name//“/}
output_file_name=${output_file_name//”/}
output_file_name=${output_file_name//\【/}
output_file_name=${output_file_name//\】/}
output_file_name=${output_file_name//；/}
output_file_name=${output_file_name//？/}
output_file_name=${output_file_name//《/}
output_file_name=${output_file_name//》/}
output_file_name=${output_file_name//\(/};
output_file_name=${output_file_name//\)/};
output_file_name=${output_file_name//「/};
output_file_name=${output_file_name//」/};
output_file_name=${output_file_name//、/};
output_file_name=${output_file_name//\~/};
output_file_name=${output_file_name//\）/};
output_file_name=${output_file_name//\（/};
output_file_name=${output_file_name//『/};
output_file_name=${output_file_name//』/};
output_file_name=${output_file_name//|/};
output_file_name=${output_file_name//_/};

output_file_name=${output_file_name//@/};
output_file_name=${output_file_name//［/};
output_file_name=${output_file_name//］/};
output_file_name=${output_file_name//\#/};


echo "output_file_name: $output_file_name";

echo "ffmpeg -i $execute_path/video.m4s -i $execute_path/audio.m4s -c:v copy -c:a aac -strict experimental $execute_path/$output_file_name.mp4";

echo "ffmpeg -i $execute_path/video.m4s -i $execute_path/audio.m4s -c:v copy -c:a aac -strict experimental $execute_path/$output_file_name.mp4" >> $execute_path/implement.sh;

bash $execute_path/implement.sh;
 
mv $execute_path/*.mp4 $execute_path/../../../;

```
