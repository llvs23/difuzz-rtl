Easy to experiment DifuzzRTL
============================

# Introduction

We modified the code so that you can easily perform multicore Fuzzing and check map-coverage about some of modules.
Other additional settings are needed for accurate operation, but we made it simple to run.

## Setup

First of all, you can enter the Docker Container using the Docker File in difuzz-rtl directory


```
docker build -t difuzzrtl .
docker run -it --name difuzzrtl difuzzrtl:latest
```

Before fuzzing, you need to setup.

```
cd Fuzzer
. ./setup.sh
```

## Instructions

### Singlecore Fuzzing
>
> A command was added to simply check the paper's mapping operation.
> 
> ```
> cd Fuzzer
> make SIM_BUILD=<build_dir> VFILE=<target> TOPLEVEL=<topmodule> NUM_ITER=<num_iter> OUT=<outdir> VALUE=<view mapping>
> ```
> **VALUE**:     Set 1 to view coverage mapping of the number of iteration
>                (The value is currently only available on RocketTile_state)
>  (e.g., make SIM_BUILD=sim_build_RocketTile VFILE=RocketTile_state TOPLEVEL=RocketTile NUM_ITER=10 OUT=out10 VALUE=1)
> 


#### Multicore Fuzzing
> 
> Multicore Fuzzing does not work for existing open source files. 
> Therefore, I made some modifications to make it work.
> 
> ```
> cd Fuzzer
> make SIM_BUILD=<build_dir> VFILE=<target> TOPLEVEL=<topmodule> NUM_ITER=<num_iter> OUT=<outdir> MULTICORE=<num_core>
> 
> ```




Also, I wanted to find out the versatility of DiffuzzRTL. So I tried fuzzing the fir file of another chip based on RocketTile through the open source DiffuzzRTL.
As a result, fuzzing is possible, but the Verilog file that came out after instrumentation may require some modification (such as porting).


I hope it will help others who want to study DiffuzzRTL in the future. 
Thank you Author, Jae-won Hur, for your great help. 
Also, look forward to the great honor of UNIST CSS lab.

