## What this repo contains

In this repo, we have analyzed 96 various versions of the blocked matrix multiplication programs on combinations of following factors.
1. Matrix size: 2048, 8192
2. Outer loop order (variants): ‘ijk’, ‘jik’, ‘jki’, ‘ikj’, ‘kij’, ‘kji’
3. Tile size: 4, 8, 16, 32, 64, 128, 256, 512

Analysis contains various performance counters including but not limited to cache-misses, TLB misses, cpu cycles, branch instructions, etc. We use perforator CLI tool for analysis.

### Perforater installation 
```bash
curl https://zyedidia.github.io/eget.sh | sh ./eget zyedidia/perforator
```
```bash
pip3 install regex pandas
```

### DELETE FOLLOWING DIRECTORIES
out2048/
out8192/
csv/

### RUN FOLLOWING PYTHON FILES IN SEQUENCE
python3 outgen2048.py // genereate .out files in out2048/
python3 execout2048.py // generate csv files in csv/

python3 outgen8192.py // genereate .out files in out2048/
python3 execout8192.py // generate csv files in csv/

### FOLLOWING COMMAND IS BEING EXECUTED
sudo ./perforator -e cpu-cycles,branch-misses,branch-instructions,cache-misses,dtlb-read-accesses,dtlb-read-accesses,dtlb-read-misses,dtlb-write-misses,l1d-read-accesses,l1d-read-misses,l1d-write-accesses,l1i-read-misses,ll-read-accesses,ll-read-misses,ll-write-accesses,ll-write-misses -r multiplication --csv ./out2048/v3_2048_32 > csv/v3_2048_32.csv