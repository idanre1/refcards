# split pcap file
-C 100 -> 100MB file splt
```bash
tcpdump -r old_file.pcapng -w new_files -C 100
```
