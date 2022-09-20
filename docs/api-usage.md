# API Usage

## Using RedactKit's core library as an API to write custom python scripts

RedactKit comes packaged with Python runtime. You can choose to use RedactKit's core redaction patterns as an API to write your own Python script if you wish to.

To do so: Run `python` in your powershell terminal and import redactkit as below.

```python
from gtredactkit import runner
data = """this is my IP: 102.23.5.1
My router is : 10.10.10.1
71.159.188.33
81.141.167.45
165.65.59.139
64.248.67.225
https://tech.gov.sg
My email is harold@mail.com
this is my IP: 102.23.5.1
My router is: 10.10.10.1
71.159.188.33
81.141.167.45
165.65.59.139
64.248.67.225
Base64 data
QVBJX1RPS0VO
UzNjcjN0UGFzc3dvcmQ=
U3VwM3JTM2NyZXRQQHNzd29yZA==
Singapore NRIC
G0022121F
F2121200F
G1021022E
S1022221L
G1222221C
S0000212Q
F2120212E
S0021001P
"""
sensitive_data_list = runner.api_identify_sensitive_data(data)
print(sensitive_data_list)

""" ['102.23.5.1', '10.10.10.1', '71.159.188.33', '81.141.167.45', '165.65.59.139', '64.248.67.225', 'https://tech.gov.sg', 'harold@mail.com', 'mail.com', '102.23.5.1', '10.10.10.1', '71.159.188.33', '81.141.167.45', '165.65.59.139', '64.248.67.225', 'QVBJX1RPS0VO', 'UzNjcjN0UGFzc3dvcmQ=', 'U3VwM3JTM2NyZXRQQHNzd29yZA==', 'G0022121F', 'F2121200F', 'G1021022E', 'S1022221L', 'G1222221C', 'S0000212Q', 'F2120212E', 'S0021001P'] """
```

[Go back to main page](./readme.md)
