[![Build Status](https://travis-ci.org/pynetscript/serial-lookup.svg?branch=master)](https://travis-ci.org/pynetscript/serial-lookup)
[![GitHub release](https://img.shields.io/badge/version-1.1-blue.svg)](https://github.com/pynetscript/serial-lookup)
[![license](https://img.shields.io/github/license/pynetscript/serial-lookup.svg)](https://github.com/pynetscript/serial-lookup/blob/master/LICENSE)

# serial-lookup

```
Written by:           Aleks Lambreca
Creation date:        08/04/2018
Last modified date:   08/04/2018
Version:              v1.1

Script use:           Parses a Cisco serial number into an approximate manufacture date.
                      The script needs 2 arguments to run:
                      - 1st argument: serial-number.py
                      - 2nd argument: SERIALNUMBER
                      Valid command looks like:
                      ./serial-number.py SAD08300D4W

Script input:         Cisco serial number

Script output:        Approximate manufacture date
                      Travis CI build notification to Slack private channel
```

# .travis.yml

- [Travis CI](https://travis-ci.org/pynetscript/serial-lookup)
- What language: **Python**
- What versions: **2.7** , **3.4** , **3.5** , **3.6**
- What to run: **python serial-lookup.py**
- Where to send notifications: **pynetscript:3GF5L6jlBvYl9TA5mrcJ87rq** 
  - Install Travis CI on [Slack](https://pynetscript.slack.com) and at some point it will output a slack channel to use.
  - Replace **pynetscript:3GF5L6jlBvYl9TA5mrcJ87rq** with your own channel.
  - Supports private channels.
  

# 2nd argument ('Serial Number')

https://tinyurl.com/y8sudxjy

**Manufacturing Year Codes:**

|Cisco Code | Manufacturing Year|
|-----------|-------------------|
|01|1997| 
|02|1998|
|03|1999|
|04|2000|    
|05|2001|    
|06|2002|
|07|2003|
|08|2004|
|09|2005|
|10|2006|
|11|2007|
|12|2008|
|13|2009|
|14|2010|
|15|2011|
|16|2012|
|17|2013|
|18|2014|
|19|2015|
|20|2016|
|21|2017|
|22|2018|
|etc.|etc.|
   
**Manufacturing Week Codes:**


|Cisco Code | Calendar Month|
|-----------|---------------|
|01-05 | January|
|06-09 | February| 
|10-14 | March|
|15-18 | April|
|19-22 | May|
|23-27 | June|
|28-31 | July|
|32-35 | August|
|36-40 | September|
|41-44 | October|
|45-48 | November| 
|49-52 | December|

The serial number will be in the format: 'LLLYYWWSSSS'
- 'YY' is the year of manufacture
- 'WW' is the week of manufacture. 

Example S/N: 'SAD08300D4W'
- 'YY' = 08 (year code)
- 'WW' = 30 (week code)
  
  
# 1st argument (serial-number.py)
  
This is the script that we will run.   
Legal examples:   
- `python2 <1st_argument> <2nd_argument>`
- `python3 <1st_argument> <2nd_argument>`

Let's use the following example to explain the script:    
- `python3 serial-lookup.py SAD08300D4W`

The script will:     
- Count the characters from the Serial Number we specified (SAD08300D4W)
  - If lower than 11 characters we get an error and the script stops.
  - If not, continue.
- Parse the year code.
- Parse the week code.
- Create Cisco's manufacturing years list (from year 1996 up to 2100).
- Create a dictionary that maps Cisco's year codes to Cisco's manufacturing years.
- Create a dictionary that maps Cisco's week codes to calendar Months.
- Print the Serial Number that was specified (SAD08300D4W).
- If parsed year code in dictionary, put it into variable "year".
- If parsed year code not in dictionary, print error ">> Error: Could not match year code!" and put nothing into variable "year".
- If parsed week code in dictionary, put it into variable "week".
- If parsed week code not in dictionary, print error ">> Error: Could not match week code!" and put nothing into variable "week".
- Finally the script will print ">> Approximate manufacture date: **week** **year**".
