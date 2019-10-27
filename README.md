## Build with cmake

## Build with make only 

see [uwsampa/graphbench/data/generator](https://github.com/uwsampa/graphbench/tree/master/data/generator). 

```
make all
```

## Run 

-- generator_seq

```
./generator_seq <# of vertices (log 2 base)> <-e intNumber [optional: average # of edges per vertex, defualt to be 16> <-o outputFileName [optional: default to stdout]> <-s intName [optional: default to use the current time]> <-b [optional: default is ascii version, -b for binary version]>
```

-- generator_omp

```
./generator_omp <# of vertices (log 2 base)> <-e intNumber [optional: average # of edges per vertex, defualt to be 16> <-o outputFileName [optional: default to stdout]> <-s intName [optional: default to use the current time]> <-b [optional: default is ascii version, -b for binary version]>
```

## Example

To produce a data file with 2^16 vertices and an average of 4 edges per vertex, with tsv output, do:

```
./generator_omp	16 -e 4 -o output16.txt
```
