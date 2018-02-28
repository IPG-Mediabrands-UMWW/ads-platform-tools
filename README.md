# ads-platform-tools

Tools and utilities for the Twitter Ads Platform. 

Also useful, see https://github.com/twitterdev/ton-upload for using the TON API.

## Installation

Clone the repository:

```
$ git clone https://github.com/twitterdev/ads-platform-tools.git
$ cd ads-platform-tools/
```

If using the Python tools, install the following packages:

```
$ pip install -r python/requirements.pip
```

## Usage

The following examples assume `ads-platform-tools/` is the working directory.

### hash_tailored_audience_file

Sample tools to hash data for tailored audience uploads, in either `Python` or
`Perl`. Details on these normalization rules can be found
[here](https://business.twitter.com/en/help/campaign-setup/campaign-targeting/tailored-audiences.html) or
[here](https://developer.twitter.com/en/docs/ads/audiences/overview/file-data).

Data types supported:
 - MOBILEDEVICEID
 - IDFA
 - ADID
 - ANDROID
 - EMAIL
 - PHONE
 - TWITTERID
 - TWITTERSCREENNAME

Python:

```
$ python python/hash_tailored_audience_file.py --type EMAIL --infile path/to/emails_source.txt --outfile path/to/emails_hashed.txt
```

Perl:

```
$ perl perl/hash_tailored_audience_file.pl EMAIL path/to/emails_source.txt
```

### hash_mact_device

Sample script to debug the HMAC hashing of MACT device_ids. Input is a single,
unhashed normalized device_id and output will include both the hashed device id
and the hashed extra device id.

Python:

```
$ python python/hash_mact_device.py --env prod --value abc123456789
```

### fetch_stats

Sample script implementing [best practices](https://developer.twitter.com/en/docs/ads/analytics/overview/best-practices)
for pulling ads analytics for an advertiser account.

Python:

```
$ python python/fetch_stats.py -a abc1
```

Params:

```
-a abc1   # the :account_id to run the stats fetcher on
-s        # pull segmented stats
-v        # output avg query costs
-vv       # output stats API calls made
```

Sample output:

```
Best practices stats check for :account_id abc1
-----------------------------------------------
Current time:   2015-04-16 02:32:16.815510
Start time:     2015-04-09 02:00:00
End time:       2015-04-16 01:59:59
-----------------------------------------------
Pre-filtered data:          2
Funding instruments:        1
Pre-filtered data:          15381
Campaigns:                  67
Pre-filtered data:          14768
Line items:                 37
Pre-filtered data:          11518
Promoted Tweets:            33
    fetching stats for 37 line items
    fetching stats for 33 promoted tweets
-----------------------------------------------
Total Stats Queries:        4
Total Stats Request Cost:   2780
Queries Rate Limited:       0
-----------------------------------------------
Time elapsed:           11.44861
```
