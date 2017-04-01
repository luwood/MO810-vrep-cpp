# C++ V-REP Remote API client

MO810/MC959 - 1s2017 - C++ Example code. 


## Compile instructions

This project is build using cmake.

```
# Set a environment variable called VREP_PATH poiting to the directory of V-REP. 
# The execute cmake
VREP_PATH=/home/danlu/Applications/V-REP_PRO_EDU_V3_3_2_64_Linux cmake .
```

You will only need to execute this once. 
Now you can use make as you would normaly use in other projects. 

```
make

# You will find the executable in the bin/ folder 
bin/cli

# To clean up
make clean
```

## Execute 
Start V-REP and load the scene: scenes/p3dx.ttt. 
Now execute bin/cli


