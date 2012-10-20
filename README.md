monitor
=======

process monitoring in nodejs

Example Config for a process:
<pre>
<code>
{
  "start":"",
  "stop":"",
  "pid_file":"",
  "service_location":"",
  "port":"",
  "scripts":{
    "free disk":"rm -rf ./notneeded.txt",
    "free ram":"ls -ahl"
  },
  "check":{
     "port":{
        "type":"tcp",
        "attempts":3,
        "onSingleFail":"restart",
        "failed":"alert, stop"
     }, 
     "pid":{
       "attempts":4,
       "onSingleFail":"restart",
       "failed":"alert stop"
     },
     "disk":{
        "usage":"> 50%",
        "attempts":1,
        "onSingleFail":"alert, script:free disk",
        "failed":"stop",
        "success":"alert"
      },
     "cpu":{
        "usage":"> 60%",
        "attempts":5,
        "onSingleFail":"alert, restart",
        "failed":"stop"
     },
     "ram":{
        "usage":"> 20MB",
        "attempts":"5",
        "onSingleFail":"alert, restart",
        "failed":"restart, alert, script:free ram"
     }
  }

}
</code>
</pre>