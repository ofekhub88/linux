Count interval time 
=====================

d1=$(date -d "$1" +%s)
d2=$(date -d "$2" +%s)

echo $(( (d1 - d2))   # second
