# Facebook News Scraper

## Overview
Dataset contains **19,850** posts from **83** various news organizations & personalities representing up to the last 250 page posts made as of July 14th, 2017. Each post has up to 100 comments for a total of **1,025,403** comments.

You can alternatively access the data through BigQuery:
https://bigquery.cloud.google.com/dataset/jbencina-144002:fb_news

## Updates
2021-10-10: Updated reame
2019-11-21: Updated the comments data to obfuscate user id and user name with hashed values using Python's blake2b

## Files
- post_scraper_github.py - script used to scrape pages
- fb_news_comments_1000K.7z - comments file
- fb_news_posts_20K.csv - posts file
- fb_news_pagenames.csv - page names

Apologizes for the 7Z format, but it compressed the best.

## Script
This script loops though a dictionary of Facebook page ids and retrieves the last N posts and up to 100 comments for each post. The results are optionally cached as individual data files and ultimately stored as a set of data frames: one for posts, one for comments. They can be linked by the common post_id field.

While originally used for news sites, this script can accommodate any Facebook page. One could also loop though the comments to get more than the last 100.

## Usage
To join the two datasets, split the `post_id` and `post_name` fields from
the Posts and Comments files respectively on underscore. The resulting ID
allows for a clean join between both files.

## Fields - Posts
- created_time
- description: only for posts with links
- link
- message: post contents
- page_id
- post_id: two part identifier of [page_id]_[post_id]
- react_angry
- react_haha
- react_like
- react_love
- react_sad
- react_wow
- scrape_time
- shares

## Fields - Comments
- created_time
- from_id: user id (obfuscated)
- from_name: publicly visible user name (obfuscated)
- message: text
- post_name: two part identifier of [from_id]_[post_id]

## Pages Scraped
May be subject to future additions.


    'bbc': '228735667216',
    'fox_news': '15704546335',
    'abc_news': '86680728811',
    'nbc_news': '155869377766434',
    'cbs_news': '131459315949',
    'cnn': '5550296508',
    'msnbc': '273864989376427',
    'npr': '10643211755',
    'politico': '62317591679',
    'reuters': '114050161948682',
    'wastington_post': '6250307292',
    'ny_times': '5281959998',
    'economist': '6013004059',
    'financial_times': '8860325749',
    'the_guardian': '10513336322',
    'daily_mail': '164305410295882',
    'ny_dailynews': '268914272540',
    'breitbart': '95475020353',
    'infowars': '80256732576',
    'huffington_post': '18468761129',
    'daily_kos': '43179984254',
    'salon': '120680396518',
    'the_hill': '7533944086',
    'national_review': '15779440092',
    'usa_today': '13652355666',
    'wsj': '8304333127',
    'buzzfeed_news': '618786471475708',
    'cnbc': '97212224368',
    'newsweek': '18343191100',
    'associated_press': '249655421622',
    'bloomberg_politics': '1481073582140028',
    'yahoo_news': '338028696036',
    'chicago_tribune': '5953023255',
    'la_times': '5863113009',
    'daily_beast': '37763684202',
    'drudge_report': '1416139158459267',
    'the_blaze': '140738092630206',
    'young_cons': '147772245840',
    'daily_caller': '182919686769',
    'newsmax': '85452072376',
    'wordl_net_daily': '119984188013847',
    'independent_journal_review': '687156898054966',
    'los_angeles_times': '5863113009',
    'time': '10606591490',
    'us_worldnews_report': '5834919267',
    'business_insider': '20446254070',
    'slate': '21516776437',
    'vox': '223649167822693',
    'think_progress': '200137333331078',
    'democratic_undergound': '455410617809655',
    'talking_points_memo': '98658495398',
    'the_nation': '7629206115',
    'mother_jones': '7642602143',
    'raw_story': '20324257234',
    'pro_publica': '13320939444',
    'townhall': '41632789656',
    'washington_examiner': '40656699159',
    'daily_signal': '300341323465160',
    'weekly_standard': '11643473298',
    'the_atlantic': '29259828486',
    'the_newyorker': '9258148868',
    'morning_joe': '90692553761',
    'vice_news': '235852889908002',
    'rt': '326683984410',
    'al_jazeera': '7382473689',
    'one_america_news': '220198801458577',
    'christian_science_monitor': '14660729657',
    'pbs_newshour': '6491828674',
    'miami_herald': '38925837299',
    'person_alex_jones': '6499393458',
    'person_anderson_cooper': '60894670532',
    'person_rachel_maddow': '25987609066',
    'person_sean_hannity': '69813760388',
    'person_chris_matthews': '114114045339706',
    'person_megyn_kelly': '1425464424382692',
    'person_neil_cavuto': '101988643193353',
    'person_chris_hayes': '153005644864469',
    'person_shepard_smith': '131010790489',
    'person_erin_burnett': '102938906478343',
    'person_joe_scarobourgh': '144128236879',
    'person_rush_limbaugh': '136264019722601',
    'person_bill_mahar': '62507427296',
    'person_ann_coulter': '695526053890545'
