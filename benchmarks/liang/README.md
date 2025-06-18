# Benchmarks
This folder contains code to replicate the benchmarks from the paper.


```
# require to create the dataset before 
mkdir plot data
NB_FEATURE=100
for trial in {0..100}; do python sim_liang.py $trial $NB_FEATURE; done
for trial in {0..100}; do python sim_liang.py $trial $NB_FEATURE --cv 10; done
for trial in {0..100}; do python sim_liang.py $trial $NB_FEATURE --robust 10; done
for trial in {0..100}; do python sim_liang.py $trial $NB_FEATURE --cv 10 --robust 10; done

python sim_liang_agg.py
python sim_liang_model.py

```