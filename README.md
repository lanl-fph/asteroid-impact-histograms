# Deep Water Asteroid Impact Dataset — Histogram Data

[![License](https://licensebuttons.net/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0/)

```
XX              XXXXX XXX         XX XX           XX       XX XX XXX         XXX
XX             XXX XX XXXX        XX XX           XX       XX XX    XX     XX   XX
XX            XX   XX XX XX       XX XX           XX       XX XX      XX XX       XX
XX           XX    XX XX  XX      XX XX           XX       XX XX      XX XX       XX
XX          XX     XX XX   XX     XX XX           XX XXXXX XX XX      XX XX       XX
XX         XX      XX XX    XX    XX XX           XX       XX XX     XX  XX
XX        XX       XX XX     XX   XX XX           XX       XX XX    XX   XX
XX       XX XX XX XXX XX      XX  XX XX           XX XXXXX XX XX XXX     XX       XX
XX      XX         XX XX       XX XX XX           XX       XX XX         XX       XX
XX     XX          XX XX        X XX XX           XX       XX XX         XX       XX
XX    XX           XX XX          XX XX           XX       XX XX          XX     XX
XXXX XX            XX XX          XX XXXXXXXXXX   XX       XX XX            XXXXXX
```

This dataset contains 2D and 3D histograms derived from the LANL deep water asteroid impact dataset (LA-UR-17-21595). The source dataset includes 12 timesteps, each with 27 million rows and three columns: rowid, v02, and v03. The 2D histograms are computed from (`rowid`, `v02`) and (`rowid`, `v03`) pairs, while the 3D histograms are generated from (`rowid`, `v02`, `v03`) triples (TODO).

All histograms are stored in Apache Parquet, with each row representing a single histogram bucket. In the case of 2D histograms, each row contains five columns: `x-min`, `x-max`, `y-min`, `y-max`, and `counts`. Here, `[x-min, x-max)` defines the value range for the first dimension, `[y-min, y-max)` defines the range for the second dimension, and `counts` records the number of elements in the bucket.

Here is an example of a 2D histograms:

```
File path:  pv_insitu_300x300x300_00000_2dxp_rowid_v02.parquet
Created by: AirMettle
Schema:
message schema {
  optional double x-min;
  optional double x-max;
  optional double y-min;
  optional double y-max;
  optional int32 counts (INTEGER(32,false));
}


Row group 0:  count: 210  18.51 B records  start: 4  total(compressed): 3.797 kB total(uncompressed):3.797 kB 
--------------------------------------------------------------------------------
        type      encodings count     avg size   nulls   min / max
x-min   DOUBLE    _ _ R     210       8.07 B     0       "-0.0" / "2.5165824E7"
x-max   DOUBLE    _ _ R     210       8.07 B     0       "-0.0" / "2.9360128E7"
y-min   DOUBLE    _ _ R     210       0.30 B     0       "-0.0" / "1.015625"
y-max   DOUBLE    _ _ R     210       0.30 B     0       "-0.0" / "1.015869140625"
counts  INT32     _ _ R     210       1.78 B     0       "1" / "3447584"
```

Note that all 2D histograms are named in the form of:

`pv_insitu_300x300x300_<timestep>_2dxp_<dimension1>_<dimension2>.parquet`.


# Acknowledgement

This sample dataset is prepared by an employee of Triad National Security, LLC which operates Los Alamos National Laboratory for the U.S. Department of Energy/National Nuclear Security Administration.
