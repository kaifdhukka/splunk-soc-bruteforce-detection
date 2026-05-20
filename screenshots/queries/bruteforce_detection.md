# SSH Brute Force Detection Query

```spl
index=* "Failed password"
| rex "Failed password for (invalid user )?(?<target_user>\w+) from (?<src_ip>\d+\.\d+\.\d+\.\d+)"
| stats count by src_ip, target_user, host
| where count >= 5
```
