### About the voter file geocoding process
The team aimed to use the voter file after 2022's primary registration has closed. Since geocoding all the voter addresses in the entire state is time consuming, the team used an old version of the voter file first. <br>

The raw notebook is [here](https://github.com/NPR-investigations/SB_202_analysis/blob/main/20220421_dropbox_voting_files.ipynb). It's quite messy because geocoding ~3.5 million addresses took a long time and we used several different approaches.<br>
One is using census's one-line address api:<br>
```
voter2['url'] = ['https://geocoding.geo.census.gov/geocoder/locations/onelineaddress?address=' + x + '&benchmark=2020&format=json' for x in voter2.onelineaddress]
```
<br>It's extremely slow. So we switched to [Census Batch Geocoder](https://pypi.org/project/censusgeocode/).<br>

We split the voter file into batches of 10,000 addresses...to_geocode is the dataframe containing addresses to be geocoded<br>

```
batchcount = len(addrmerge[pd.isna(addrmerge.processed) == True])//10000+1\n

addrbatch = np.array_split(to_geocode, batchcount)

for batch in addrbatch:
    order = next(i for i, j in enumerate(addrbatch) if j is batch)
    filepath = 'batch_geocoding/20220502_batch_' + str(order) + '_of_' + str(batchcount) + '.csv'
    batch.to_csv(filepath, header = False)
```

We also used R's census geocoder for some of the addresses at one point. <br>

Fast forward to late May of 2022, the voter registration window for the primary closed, so we purchased the latest [voter rolls from Georgia Secretary of State](https://sos.ga.gov/page/order-voter-registration-lists-and-files), and stitched it together with the old addresses. Turns out that most addresses have been geocoded and we were able to geocode the rest relatively quickly. The notebook that does the stitching is [here](https://github.com/NPR-investigations/SB_202_analysis/blob/main/20220503_geocoding_current_voter_file_fill_null.ipynb)
