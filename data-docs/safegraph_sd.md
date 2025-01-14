**Meta Data Name**: Safegraph Social Distancing Data

**Last Modified**: 2/22/2021

**Author**: Andres Crucetta Nieto

### Data Location: 

Safegraph Social Distancing data can be accessed via their [COVID-19 data consortium signup](https://www.safegraph.com/covid-19-data-consortium).

### Data Source(s) Description:  
Source is [here](https://docs.safegraph.com/docs/social-distancing-metrics) via Safegraph. 

### Description of Data Source Tables: 
The data was generated using a panel of GPS pings from anonymous mobile devices. We determine the common nighttime location of each mobile device over a 6 week period to a Geohash-7 granularity (~153m x ~153m). For ease of reference, we call this common nighttime location, the device's "home". We then aggregate the devices by home census block group and provide the metrics set out below for each census block group. [1]

### Description of Data Processing: 
TBD

### Key Variable and Definitions:

Safegraph Data Schema

| Variable | Variable ID in .csv | Description |
|:---------|:--------------------|:------------|
| Readable Name | Column Name | Description |

### Data Limitations:
To preserve privacy, we apply differential privacy to all of the device count metrics other than the device_count. This may cause the exact sum of devices to not equal device_count, especially for sparsely populated origin_census_block_group. Differential privacy is applied to all of the following columns: completely_home_device_count, part_time_work_behavior_devices, full_time_work_behavior_devices, delivery_behavior_devices, at_home_by_each_hour, bucketed_away_from_home_time, bucketed_distance_traveled, bucketed_home_dwell_time, bucketed_percentage_time_home. [1]

If as a result of the differential privacy applied:

    device_count < part_time_work_behavior_devices + full_time_work_behavior_devices +completely_home_device_count or
    device_count < sum(counts in bucketed_distance_traveled) or
    device_count < sum(counts in bucketed_home_dwell_count),

we then increase the device_count to the applicable sum (this only occurs in census_block_groups with small device_counts).

### Comments/Notes:

### References:
[1] https://docs.safegraph.com/docs/social-distancing-metrics
