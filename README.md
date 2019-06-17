# OCCompose
opensource COBOL SMAPLES with Open COBOL ESQL on docker-compose

# overview
If you have docker compose's environment, you can try this sample right away.
In this sample, you can experience the collaboration between COBOL and PostgreSQL using opensource COBOL and Open COBOL ESQL.

# Try this

* Get project from github.
```
git clone https://github.com/opensourcecobol/opensource-cobol-devel.git
cd opensource-cobol-devel/
```

* Run container images.
```
docker-compose up -d
```

* Create DB on postgresql server.
```
docker-compose exec db createdb -U postgres testdb
```

* Enter the oscobol container, compile and run COBOL Application.
```
docker-compose exec oscobol /bin/bash
```
```
ocesql src/INSERTTBL.cbl INSERTTBL.pre
cobc -locesql INSERTTBL.pre
ocesql src/FETCHTBL.cbl FETCHTBL.pre
cobc -locesql FETCHTBL.pre
```

* Test data is Inserted and fetched.
```
[root@e8ccda101772 oscobol]# cobcrun INSERTTBL
*** INSERTTBL STARTED ***
NOTICE:  table "emp" does not exist, skipping
*** INSERTTBL FINISHED ***
[root@e8ccda101772 oscobol]# cobcrun FETCHTBL
*** FETCHTBL STARTED ***
TOTAL RECORD: 0012
---- -------------------- ------
NO   NAME                 SALARY
---- -------------------- ------
0001 HOKKAI TARO             400
0002 AOMORI JIRO             350
0003 AKITA SABURO            300
0004 IWATE SHIRO            -250
0005 MIYAGI GORO            -200
0006 FUKUSHIMA RIKURO        150
0007 TOCHIGI SHICHIRO       -100
0008 IBARAKI HACHIRO          50
0009 GUMMA KURO             -200
0010 SAITAMA JURO            350
0046 KAGOSHIMA ROKURO       -320
0047 OKINAWA SHICHIRO        480
*** FETCHTBL FINISHED ***
```

Copyright 2019, Tokyo System House Co., Ltd. <opencobol@tsh-world.co.jp>
