# ohw22-proj-kerchunk
Repository for prototyping kerchunking of open AWS datasets.

### Collaborators

- Paul Branson
- Sean Harkins
- Chuck Daniels
- Aimee Barciauskas
- Alex Mandel
- Anthony Lukach

### Background

So you found an open data bucket with a heap of data you want to analyse. Maybe it is dense grids of numerical model data at global scale in NetCDF format or a stack of daily satellite earth observation TIFF files. If only you could just open them all as if they were **one** dataset.... Well maybe you can! The [Kerchunk](https://github.com/fsspec/kerchunk) library builds on top of the fsspec library and provides a interface via [Zarr](https://github.com/zarr-developers/zarr-python) to create an [XArray](https://github.com/pydata/xarray) dataset _overlay_ that can span many files stored in object storage.

Analysing a large stack of dense array data stored in open data buckets with traditional libraries can be hard, slow and sometimes not even possible. Whilst in an ideal world, datasets would be published in an _Analysis Ready_ format, this is frequently not the case and not universally possible due to the variety of access patterns that may preclude a notionally _ideal_ chunking layout. 

Given that these datasets are **large**, owned by someone else and many researchers have limited organisational capacity to rechunk and mirror such large datasets, solutions that enhance the ability to analyse published datasets 'as-is' [are valuable](https://medium.com/pangeo/cloud-performant-reading-of-netcdf4-hdf5-data-using-the-zarr-library-1a95c5c92314). Recent examples [here](https://medium.com/pangeo/fake-it-until-you-make-it-reading-goes-netcdf4-data-on-aws-s3-as-zarr-for-rapid-data-access-61e33f8fe685) and [here](https://github.com/IOMRC/intake-aodn) of such an approach are spurring a flurry of activity of people 'kerchunk'-ing available datasets as evidenced by the burgeoning kerchunk issues list!

But once a dataset has been kerchunk-ed once, others could use that index - they typically compress considerably into small (<100 MB) files that could be shared for others to reuse or to feed into a Pangeo-Forge [recipe](https://pangeo-forge.readthedocs.io/en/latest/pangeo_forge_recipes/index.html).

### Goals

1. Build an understanding of how kerchunk works (Done)
2. Identify some priority open data datasets to kerchunk (Done)
3. Test out a few file storage options for kerchunk indexes (Didnt get to)
5. Discuss options for sharing a kerchunk index (Didnt get to)
6. Create a pangeo-forge recipe. See https://github.com/pangeo-forge/staged-recipes/issues/173 (In Progress) 

Progress towards to the goals was tracked using github issues:
https://github.com/oceanhackweek/ohw22-proj-kerchunk/issues

### Datasets

Himawari 8 Sea Surface Temperature (https://registry.opendata.aws/noaa-himawari/)

### Workflow

1. Identify datasets
2. Examine dataset file format and internal chunking
3. Generate kerchunk index
4. Analyse dataset with [GCM-Fitlers](https://gcm-filters.readthedocs.io/en/latest/)

### References
1. [OHW Project Proposal](https://github.com/oceanhackweek/discussions/discussions/8)
2. https://github.com/fsspec/kerchunk
3. https://pangeo-forge.readthedocs.io/en/latest/
4. https://www.frontiersin.org/articles/10.3389/fclim.2021.782909/full 
