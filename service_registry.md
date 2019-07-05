# Service 등록

## 서비스 등록 방법
서비스 등록 하는 방법 설명
1. 서비스 정보 등록 및 Pull request
2. 관리자 서비스 등록 반영
3. 테스트 방법
4. ...

### Service Infomaton

Sample #1
서비스 등록할 정보 설명
1. service id : 등록할 서비스의 고유 ID
2. name : 서비스의 이름. Keepin 앱에 노출됨
3. descritpion : 서비스의 설명. Keepin 앱에 노출됨
4. icon url : 서비스 아이콘 url. Keepin 앱에 노출됨
5. android package name : keepin 앱에서 해당 서비스 앱을 launch 하거나 playstore 로 install 를 유도할 때 사용
6. iOS application id : appstore 로 install 를 유도할 때 사용
6. web url : web 서비스 인 경우 서비스 url

index | service id | name | description | icon url | Android package name | iOS applcation id | Web url
------|------------|------|-------------|----------|----------------------|-------------------|----------
1     | com.coinplug.metasafe | metaSAFE<br>ko:메타세이프 | Coinplug CryptoCurrency Assurance Services<br>ko:코인플러그 암호화폐 자산 보장 서비스 | http:// | com.coinplug.metasafe | id393993993 | https://raw.githubusercontent.com/METADIUM/static/master/service/image/MetaSafe.png

Sample #2
Application Basic Infomation

index | service id | name | description | icon url
------|------------|------|-------------|----------
1     | com.coinplug.metasafe | metaSAFE<br>ko:메타세이프 | Coinplug CryptoCurrency Assurance Services<br>ko:코인플러그 암호화폐 자산 보장 서비스  | http://

Application Interaction Information

index | service id | Android package name | iOS applcation id | Web url
------|------------|----------------------|-------------------|----------
1     | com.coinplug.metasafe | com.coinplug.metasafe | id393993993 | 


### iOS pre register scheme

scheme 을 왜 등록하고 어떻게 등록해야 하는지 설명

index | scheme        | service id
------|---------------|------------
1     | kp-0000000001 | com.coinplug.metasafe
2     | kp-0000000002 |
3     | kp-0000000003 |
4     | kp-0000000004 |
5     | kp-0000000005 |
6     | kp-0000000006 |
7     | kp-0000000007 |
8     | kp-0000000008 |
9     | kp-0000000009 |
10    | kp-0000000010 |
11    | kp-0000000011 |
12    | kp-0000000012 |
13    | kp-0000000013 |
14    | kp-0000000014 |
15    | kp-0000000015 |
16    | kp-0000000016 |
17    | kp-0000000017 |
18    | kp-0000000018 |
19    | kp-0000000019 |
20    | kp-0000000020 |
21    | kp-0000000021 |
22    | kp-0000000022 |
23    | kp-0000000023 |
24    | kp-0000000024 |
25    | kp-0000000025 |
26    | kp-0000000026 |
27    | kp-0000000027 |
28    | kp-0000000028 |
29    | kp-0000000029 |
30    | kp-0000000030 |
31    | kp-0000000031 |
32    | kp-0000000032 |
33    | kp-0000000033 |
34    | kp-0000000034 |
35    | kp-0000000035 |
36    | kp-0000000036 |
37    | kp-0000000037 |
38    | kp-0000000038 |
39    | kp-0000000039 |
40    | kp-0000000040 |
41    | kp-0000000041 |
42    | kp-0000000042 |
43    | kp-0000000043 |
44    | kp-0000000044 |
45    | kp-0000000045 |
46    | kp-0000000046 |
47    | kp-0000000047 |
48    | kp-0000000048 |
49    | kp-0000000049 |
50    | kp-0000000050 |
51    | kp-0000000051 |
52    | kp-0000000052 |
53    | kp-0000000053 |
54    | kp-0000000054 |
55    | kp-0000000055 |
56    | kp-0000000056 |
57    | kp-0000000057 |
58    | kp-0000000058 |
59    | kp-0000000059 |
60    | kp-0000000060 |
61    | kp-0000000061 |
62    | kp-0000000062 |
63    | kp-0000000063 |
64    | kp-0000000064 |
65    | kp-0000000065 |
66    | kp-0000000066 |
67    | kp-0000000067 |
68    | kp-0000000068 |
69    | kp-0000000069 |
70    | kp-0000000070 |
71    | kp-0000000071 |
72    | kp-0000000072 |
73    | kp-0000000073 |
74    | kp-0000000074 |
75    | kp-0000000075 |
76    | kp-0000000076 |
77    | kp-0000000077 |
78    | kp-0000000078 |
79    | kp-0000000079 |
80    | kp-0000000080 |
81    | kp-0000000081 |
82    | kp-0000000082 |
83    | kp-0000000083 |
84    | kp-0000000084 |
85    | kp-0000000085 |
86    | kp-0000000086 |
87    | kp-0000000087 |
88    | kp-0000000088 |
89    | kp-0000000089 |
90    | kp-0000000090 |
91    | kp-0000000091 |
92    | kp-0000000092 |
93    | kp-0000000093 |
94    | kp-0000000094 |
95    | kp-0000000095 |
96    | kp-0000000096 |
97    | kp-0000000097 |
98    | kp-0000000098 |
99    | kp-0000000099 |
100   | kp-0000000100 |
