## Build with cmake

* assume `~/yche-bin` exists, otherwise `mkdir -p ~/yche-bin`
*`option` (not-build-legacy-makefile), `-DLEGACY_BUILD=OFF`， otherwise `-DLEGACY_BUILD=ON`

```
rm -rf ~/build-tmp
mkdir -p ~/build-tmp 
cd ~/build-tmp
cmake -H~/workspace/yche/git-repos/Graph500KroneckerGraphGenerator -B~/build-tmp -DCMAKE_INSTALL_PREFIX=~/yche-bin
make -j
make install
```

## Build with make only 

see [uwsampa/graphbench/data/generator](https://github.com/uwsampa/graphbench/tree/master/data/generator). 

```
make all
```

## Run 

* example under the `yche-bin` folder

```zsh
./yche_generator_omp 23 -e 16 -o /ssd/zlai/yche-datasets/kron23-16.bin -b 
```

-- generator_seq

```
./generator_seq <# of vertices (log 2 base)> <-e intNumber [optional: average # of edges per vertex, defualt to be 16> <-o outputFileName [optional: default to stdout]> <-s intName [optional: default to use the current time]> <-b [optional: default is ascii version, -b for binary version]>
```

-- generator_omp

```
./generator_omp <# of vertices (log 2 base)> <-e intNumber [optional: average # of edges per vertex, defualt to be 16> <-o outputFileName [optional: default to stdout]> <-s intName [optional: default to use the current time]> <-b [optional: default is ascii version, -b for binary version]>
```

## Example

* To produce a data file with `2^16` vertices and an average of `4` edges per vertex (degree `8`), with tsv output, do:

```
./generator_omp	16 -e 4 -o output16.txt
```

* generate binary files, turning on the switch option `-b`

```
./generator_omp 24 -e 16 -o s24.kron.bin -b
./generator_omp 28 -e 15 -o rapids-s28.e15.kron.edgelist.bin -b
./generator_omp 29 -e 10 -o rapids-s29.e10.kron.edgelist.bin -b
```