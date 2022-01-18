JavaMeldyPLugin

ThreadDump 
URL=http://<Jenkins URL > monitoring?part=threadsDump"
rm /mnt/c/tmp/OCPtthreadDump.log 
d1=$(date -d "$1" +%s)
for i in {1..500};do
  curl $URL 2>&1 |awk '/Print-Test/' RS= >>/mnt/c/tmp/OCPtthreadDump.log 
done
