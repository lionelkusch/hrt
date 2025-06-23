# Benchmarks
This folder contains code to replicate the benchmarks from the paper.


```
# require to create the dataset before 
mkdir plot data
NB_FEATURE=100
# for // use the script: sim_parallel.py 0 100 100 100 --reset --nthreads 2
for trial in {0..100}; do python sim_liang.py $trial $NB_FEATURE; done
for trial in {0..100}; do python sim_liang.py $trial $NB_FEATURE --cv 10; done
for trial in {0..100}; do python sim_liang.py $trial $NB_FEATURE --robust 10; done
for trial in {0..100}; do python sim_liang.py $trial $NB_FEATURE --cv 10 --robust 10; done
python sim_liang_agg.py # aggregate all the simulated data

# for adding result with shappley value
for trial in {0..100}; do python sim_shapley.py $trial $NB_FEATURE; done

# create robust: sweep_robust / require normal sim for having X, Y, trust
for trial in {0..100}; do python sim_robust.py $trial $NB_FEATURE --reset-models; done
python sim_robust_agg.py # aggregate the result


# require result cv, sweep_robust and normal
python sim_agg.py

# Predictor:
python sim_predictors.py 0 100 0 100 --reset --nthreads 8 # create data
python sim_predictors_agg.py # aggregate data
python sim_predictors_importance.py
python sim_predictors_order.py

# require require predictor
python sim_knockoffs.py

# helper function: sim_model.py


```
