
## How to solve

1. Enter the files folder 

2. Then try to match the checksum with all of the files inside using grep

```bash
sha256sum files/* | grep '03b52eabed517324828b9e09cbbf8a7b0911f348f76cf989ba6d51acede6d5d8'

```

```bash
    03b52eabed517324828b9e09cbbf8a7b0911f348f76cf989ba6d51acede6d5d8  files/00011a60
```

3. Decrypt the files using ./decrypt.sh

```bash
     ./decrypt.sh files/00011a60
```

picoCTF{trust_but_verify_00011a60}
    