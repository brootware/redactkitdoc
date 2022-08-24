# Usage guide

## Basic usage

You can redact a text glob from PowerShell Terminal as below.

```bash
redactor 'this is my ip:127.0.0.1. my email is broot@outlook.com. secret link is github.com'
```

This will create a redacted file and a hashshadow file which you can later use to unredact.

```json
// .hashshadow.json
{
  "5f7aa522-86e5-4ca7-83ae-09fbb5a1044b": "broot@outlook.com",
  "983b017a-98a5-4763-aa6d-a8ad69db20bc": "github.com",
  "a9581c73-05cb-428e-8c62-8bf1521a8aa1": "127.0.0.1"
}
```

```text
<!-- redacted.txt -->
this is my ip:a9581c73-05cb-428e-8c62-8bf1521a8aa1. my email is 5f7aa522-86e5-4ca7-83ae-09fbb5a1044b. secret link is 983b017a-98a5-4763-aa6d-a8ad69db20bc
```

To redact a single file from terminal.

```bash
redactor test.txt 
```

To Unredact a redacted file.

```bash
redactor redacted_test.txt -u .hashshadow_test.txt.json 
```

This will create an unredacted file which contains the original unmasked data.

```text
<!-- unredacted.txt -->
this is my ip:127.0.0.1. my email is broot@outlook.com. secret link is github.com
```

## Advance usage

You can redact multiple files in a folder with sub directories and output the files into a newly created directory.

Consider the below folder containing multiple log files with sub directory.

```bash
tree foldertoredact 
foldertoredact
├── cctest.txt
├── ip_test 3.txt
├── ip_test 4.txt
├── ip_test.txt
├── nric.txt
└── subdir
    └── ip_test copy.txt

1 directory, 6 files
```

To redact all of log files in the folder and place them in a new folder:

```bash
redactor foldertoredact -d newfolder
```

```bash
tree newfolder
newfolder
├── redacted_cctest.txt
├── redacted_ip_test 3.txt
├── redacted_ip_test 4.txt
├── redacted_ip_test copy.txt
├── redacted_ip_test.txt
└── redacted_nric.txt

0 directories, 6 files
```

Besides the core regex patterns of SG NRIC, domain names, emails, ip addresses, base64 strings and credit cards, you can also define custom regex patterns to redact them from your log files.

To redact using custom regex pattern, create a custom json file as per format below.

```bash
redactor file -c customregex.json
```

```json
// custom.json
[
    {
        "pattern": "^([a-zA-Z0-9_-]*:[a-zA-Z0-9_-]+@github.com*)$",
        "type": [
            "API Keys",
            "Credentials",
            "Bug Bounty",
            "GitHub"
        ]
    },
    {
        "pattern": "(?i)^(arn:(?P<Partition>[^:\\n]*):(?P<Service>[^:\\n]*):(?P<Region>[^:\\n]*):(?P<AccountID>[^:\\n]*):(?P<Ignore>(?P<ResourceType>[^:\\/\\n]*)[:\\/])?(?P<Resource>.*))$",
        "type": [
            "Identifiers",
            "Networking",
            "AWS",
            "Bug Bounty"
        ]
    },
    {
        "pattern": "(?i)^((facebook|fb)(.{0,20})?['\\\"][0-9a-f]{32}['\\\"])$",
        "type": [
            "API Keys",
            "Bug Bounty",
            "Credentials",
            "Facebook"
        ]
    }
]
```
