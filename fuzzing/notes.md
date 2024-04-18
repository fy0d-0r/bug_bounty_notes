## Gobuster

### Directory Fuzzing with `dir`
```
gobuster dir -h 
```

```
gobuster dir -w common.txt -u http://10.10.11.12/
gobuster dir -w big.txt -x php,txt,html -u http://10.10.11.12/
```



## FUFF
```
fuff -w common.txt:FUZZ -u http://10.10.22.33/FUZZ/?id=1234 -mc 200 -fs 1487 
-fs #[Filter Size] excludes the response with specified size # can specify multiple sizes with commas
-mc #[Match Code] #can specify multiple codes with commas

fuff -w common.txt:FUZZ1 -w values.txt:FUZZ2 -u http://10.10.22.33/FUZZ1/?id=FUZZ2 -fs 1487
# multiple placeholders with multiple wordlists
```

## WFUZZ

## Dirb
