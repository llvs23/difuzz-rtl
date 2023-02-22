Easy to experiment DifuzzRTL
============================

# Introduction

I modified the code so that you can easily perform multicore Fuzzing and check map-coverage about some of modules.


Other additional settings are needed for accurate operation such as Muticore fuzzing, but I made it simple to run.



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
> ![Finding Hash Value_2](https://user-images.githubusercontent.com/121912362/220507933-54067bae-4d96-43f6-8daa-b3698b06a3f4.jpg)
> 
> ![Finding Hash Value_1](https://user-images.githubusercontent.com/121912362/220508043-1c8bd5fe-8dbf-4600-ac6c-47bcd93fb5c0.jpg)
>
> ```
> cd Fuzzer
> make SIM_BUILD=<build_dir> VFILE=<target> TOPLEVEL=<topmodule> NUM_ITER=<num_iter> OUT=<outdir> VALUE=<view mapping>
> ```
> **VALUE**:     Set 1 to view coverage mapping of the number of iteration
>                (The value is currently only available on RocketTile_state)
>
>  (e.g., make SIM_BUILD=sim_build_RocketTile VFILE=RocketTile_state TOPLEVEL=RocketTile NUM_ITER=10 OUT=out10 VALUE=1)
>
> If you set the value, you can see the mapping process of the module through the mapping file. 
>
> Such like below figure.
> ![image](https://user-images.githubusercontent.com/121912362/220509706-b99351c1-ab46-4ed5-900c-eeb83d92bb19.png)



#### Multicore Fuzzing
> 
> Multicore Fuzzing does not work for existing open source files. 
> Therefore, I made some modifications to make it work.
>
> ※Caution 
>   you need to set NUM_ITER over 5,000 times and can't not use Multocore over 40 cores.
>
> ```
> cd Fuzzer
> make SIM_BUILD=<build_dir> VFILE=<target> TOPLEVEL=<topmodule> NUM_ITER=<num_iter> OUT=<outdir> MULTICORE=<num_core>
> ```
> (e.g., make SIM_BUILD=sim_build_RocketTile VFILE=RocketTile_state_Muticore TOPLEVEL=RocketTile NUM_ITER=5000 OUT=out10 MUTICORE=8)




Also, I wanted to find out the versatility of DiffuzzRTL. So I tried fuzzing the fir file of another chip based on RocketTile through the open source DiffuzzRTL.
As a result, fuzzing is possible, but the Verilog file that came out after instrumentation may require some modification (such as porting).


I hope it will help others who want to study DiffuzzRTL in the future. 
  
Thank you Author, Jae-won Hur, for your great help. 
  
Also, look forward to the great honor of UNIST CSS lab.

