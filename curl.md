# curl check status
=====================


 <p> Config example:


    
    curlf() {
      OUTPUT_FILE="/tmp/<FileName>.tmp"
      LOG_FILE="/tmp/<FileName>.log"
      HTTP_CODE=$(curl  --max-time 5  --silent --output $OUTPUT_FILE --write-out "%{http_code}" "$@")
      if [[ ${HTTP_CODE} -lt 200 || ${HTTP_CODE} -gt 299 ]] ; then
        cat $OUTPUT_FILE >> $LOG_FILE
        exit 22
      fi
      cat $OUTPUT_FILE|2>&1| /usr/bin/tr -d '\n'|awk '{$2=$2};1
     }
