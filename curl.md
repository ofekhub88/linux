curl check status
=====================
<p> The Code is :
curlf() {
  OUTPUT_FILE="/tmp/jmelody_out.tmp"
  LOG_FILE="/tmp/jmelody_out.log"
  HTTP_CODE=$(curl --silent --output $OUTPUT_FILE --write-out "%{http_code}" "$@")
  if [[ ${HTTP_CODE} -lt 200 || ${HTTP_CODE} -gt 299 ]] ; then
    cat $OUTPUT_FILE >> $LOG_FILE
    exit 22
  fi
  cat $OUTPUT_FILE|2>&1| /usr/bin/tr -d '\n'|awk '{$2=$2};1
}
</p>
 <p> Config example:
    
    [Service]
    Environment="HTTP_PROXY=http://proxy.example.com:80"
    Environment="HTTPS_PROXY=https://proxy.example.com:443"
    Environment="NO_PROXY=localhost,127.0.0.1,docker-registry.example.com,.corp"
 
 # insecure-registries  work wihth http 
