# split pcap file
-C 100 -> 100MB file splt
```bash
tcpdump -r old_file.pcapng -w new_files -C 100
```
-c 750000 splits every 750000 pkts
```bash
editcap -F pcapng -c 750000 old_file.pcapng split.pcapng
```
