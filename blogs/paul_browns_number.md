---
layout: post
---
<head>
<style>
em {text-align: center;}
</style>
</head>
# Finding the Paul Brown Number


## Introduction
American football is an ever evolving game where coaches use different tactics and philosophies to create a system with the singular goal of winning football games. Because of this, the sport has a tradition of tracing coaches' linage; and in the modern NFL, headcoaches' linages can be trace back to coach Paul Brown:
<p>
    <img src="https://khoabuiv.github.io/2024_headcoaches.png" alt>
    <em>Figure 1: Head Coaches Genealogy</em>
</p>
Figure 1 shows the NFL's teams' head coaches at the beginning of the 2024 season, and they all lead back to Paul Brown. Merging football with my other interest in mathematics, I decided to measure the scope's of Paul Brown influence on the NFL via "collaborative distance".


## Measuring Collaborative Distance
The mathematician Paul Erdos was the most prolific mathematicians of the 20th century, publishing around 1500 mathematical papers. To measure his influence on mathematics, Erdos' peers defined the [Erdos number](https://en.wikipedia.org/wiki/Erdős_number) to measure the collaborative distance between a mathematician and Erdos. For example:
- Erdos number 0: Erdos himself.
- Erdos number 1: Someone who wrote an article with Erdos.
- Erdos number 2: Someone who wrote an article with a person who has Erdos number 1.
- Erdos number n: Someone who wrote an article with a person who has Erdos number n-1.

## Methodology
1. Gather data from [pro-football-reference](https://www.pro-football-reference.com/). The data is consisted of all the people who coached from 1946, the year that Paul Brown started coaching professional American football, to 2023.  
2. Refine the data to only relevant information and store it in a csv file which looks like this: 
```
name,position,record,team,year
Bill Belichick,Head Coach,8-9-0,nwe,2022
```
3. Use Pandas to perform data analysis. 

## Findings: 
- There are 1227 people who coached in the NFL between 1946 and 2023.
- Out of 1227, here are the statistics about the Paul Brown's number:
    - 13 coaches with Paul Brown's number 1.
    - 99 coaches with Paul Brown's number 2.
    - 530 coaches with Paul Brown's number 3.
    - 520 coaches with Paul Brown's number 4.
    - 49 coaches with Paul Brown's number 5.
    - 2 coaches with Paul Brown's number 6.
    - 14 coaches where the Paul Brown's number is undefined.
- You can find the full JSON output [here](https://github.com/khoabuiv/Brown-s-Number-Public/blob/main/Paul_Brown_numbers.json). 
