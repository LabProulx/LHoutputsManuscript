# Coherent activity at three major lateral hypothalamic neural outputs controls the onset of motivated behavior responses

This repository includes scripts and source data that were used in the following preprint: 
__Martianova, E., Pageau, A., Pausik, N., Doucet, T., Leblanc, D, Proulx, C.D.__ [_Coherent activity at three major lateral hypothalamic neural outputs controls the onset of motivated behavior responses_](https://www.biorxiv.org/content/10.1101/2021.04.28.441785v1)

[___FiberPhotmetryDataAnalysis.ipynb___](./FiberPhotometryDataAnalysis.ipynb) notebook includes functions necessary to process, analyze, and visualize fiber photometry data. Using these functions, jupyter notebooks in the [rawData](./rawData) folder show all the steps of analysis from raw data to the final [source data](./sourceData) and plots used in the figures of the preprint. [sourceData](./sourceData) folder also includes jupyter notebooks showing stastical analysis done for the preprint.

# How to use functions

## Processing data
Using functions from [___FiberPhotmetryDataAnalysis.ipynb___](./FiberPhotometryDataAnalysis.ipynb) you can create _FiberPhotometryRecording_ object with your recordings and with one line of code get dF/F signal and create perievent arrays:

```python
# Create dictionaries with your recordings and events
signals = {'AneuronalPopulation': yourSignal_from_A,
           'BneuronalPopulation': yourSignal_from_B} # You can add as many recordings as you have from the same animal

references = {'AneuronalPopulation': yourReference_from_A, # The keys have to match the one in the signals
              'BneuronalPopulation': yourReference_from_B}
              
time_ = yourTimeVector # All your recordings and time arrays have to be the same length

events = {'event1': yourEvents1, 
          'event2': yourEvents2}
          
measurements = {'measure1': 'time': measure1time,
                          'values': measure1values}
                'measure2': 'time': measure1time,
                          'values': measure1values}
                          
# Create FiberPhotometryRecording object
r = FiberPhotometryRecording(signals,references,time_,events,
                             measurements,'mouseName','testName','trialNumber')
                             
# Calculate dF/F for all recordings
r.getdFF()
# Get a dF/F trace from one neuronal population
r.dFFs['AneuronalPopulation']

# Calculate perievent arrays for each neural population and each event
r.getPerievents()
```

