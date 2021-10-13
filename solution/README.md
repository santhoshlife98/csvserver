1. % docker run -d infracloudio/csvserver

2. % docker logs df79dd906233a83e5a1fbcf8a845e287ba65f1e5c3eaa9e1814012e9436b36aa
2021/10/13 13:30:05 error while reading the file "/csvserver/inputdata": open /csvserver/inputdata: no such file or directory 

3. % docker run -it infracloudio/csvserver bash

4. # cat <<EOF >> gencsv.sh
     #!/bin/bash

     for i in {0..9}
     do
       echo $i, $((RANDOM%100+50)) >> inputdata
     done
    EOF

5. # sh gencsv.sh

6. % docker commit 5b756cb71f49 infracloudio/csvserver:v2

7. # netstat -punta | grep csvserver

8. % docker run -t -d -p 9393:9300 infracloudio/csvserver:v2 ./csvserver

9. % docker stop e35b5b904997
