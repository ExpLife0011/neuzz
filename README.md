# NEUZZ: a neural-network assited fuzzer (S&P'19)
See S&P'19 paper [NEUZZ: Efficient Fuzzing with NeuralProgram Smoothing](https://arxiv.org/abs/1807.05620) for detail.
## Prerequisite
Tested on Ubuntu 16.04 and 18.04 with Tensorflow 1.8.0 and Keras 2.2.3
- Python 2.7
- Tensorflow
- Keras
## Build
```bash
    gcc -O3 -funroll-loops ./neuzz.c -o neuzz
```
## Usage
We use a sample program readelf as an example.
Open a terminal, start nn module
```bash
    #python nn.py [program [arguments]]
    python nn.py ./readelf -a
```
open another terminal, start neuzz module.
```bash
    #./neuzz -i in_dir -o out_dir -l mutation_len [program path [arguments]] @@
    ./neuzz -i neuzz_in -o seeds -l 7506 ./readelf -a @@  
```
If you want to try NEUZZ on a new program, 
1. Compile the new program from source code using afl-gcc.
2. Collect the training data by running AFL on the binary for a while(about an hour), then copy the queue folder to neuzz_in.
3. Follow the above two steps to start NN module and NEUZZ module.
## Sample programs
Try 10 real-world programs on NEUZZ. Check setup details at programs/[program names]/README.


