![CLEVER DATA GIT REPO](https://raw.githubusercontent.com/LiCongMingDeShujuku/git-resources/master/0-clever-data-github.png "李聪明的数据库")

# 如何查询RoboCopy输出日志文件
#### How To Query The RoboCopy Output Log File

## Contents

- [中文](#中文)
- [English](#English)
- [SQL Logic](#Logic)
- [Build Info](#Build-Info)
- [Author](#Author)
- [License](#License) 


## 中文
这里有一些SQL逻辑可以帮助你查询RoboCopy输出日志文件。切记，可以使用XML输出查询大多数内容以便使用日志文件（或大多数文本文件）。只需将内容批量插入表中，然后查询表。请记住使用FOR XML PATH（''），TYPE。


## English
Here’s some SQL logic to help you query the RoboCopy output log file. Remember; you can query most things using an XML output so for this to work with the log file (or most text files) simply bulk insert the contents into a table, and query the table. Remember to use FOR XML PATH(‘’), TYPE.

---
## Logic
```SQL
use master;
set nocount on
 
if object_id('tempdb..#robocopy_output') is not null
drop table #robocopy_output
create table #robocopy_output
(
[output] varchar(max)
)
BULK INSERT #robocopy_output
FROM 'e:load_etls_source_backupsrobocopy_log_for_load_etls_MyDatabase_01.log'
WITH
(
fieldterminator = 't'
, datafiletype = 'char'
--, fieldterminator = ','
, rowterminator = 'rn'
);
 
select * from #robocopy_output for xml path(''), type


```
Here’s what the query will look like in most cases for RoboCopy log.

![#](images/01-How-To-Query-The-RoboCopy-Output-Log-File.png?raw=true "#")

Once you click on the XML link output you’ll see the RoboCopy output file as usual. Just like you would if you clicked on the .log file from the OS.

一旦你单击XML链接输出后，会像往常一样看到RoboCopy输出文件。就像你从操作系统中单击.log文件一样。


![#](images/02-How-To-Query-The-RoboCopy-Output-Log-File.png?raw=true "#")

[![WorksEveryTime](https://forthebadge.com/images/badges/60-percent-of-the-time-works-every-time.svg)](https://shitday.de/)

## Build-Info

| Build Quality | Build History |
|--|--|
|<table><tr><td>[![Build-Status](https://ci.appveyor.com/api/projects/status/pjxh5g91jpbh7t84?svg?style=flat-square)](#)</td></tr><tr><td>[![Coverage](https://coveralls.io/repos/github/tygerbytes/ResourceFitness/badge.svg?style=flat-square)](#)</td></tr><tr><td>[![Nuget](https://img.shields.io/nuget/v/TW.Resfit.Core.svg?style=flat-square)](#)</td></tr></table>|<table><tr><td>[![Build history](https://buildstats.info/appveyor/chart/tygerbytes/resourcefitness)](#)</td></tr></table>|

## Author

- **李聪明的数据库 Lee's Clever Data**
- **Mike的数据库宝典 Mikes Database Collection**
- **李聪明的数据库** "Lee Songming"

[![Gist](https://img.shields.io/badge/Gist-李聪明的数据库-<COLOR>.svg)](https://gist.github.com/congmingshuju)
[![Twitter](https://img.shields.io/badge/Twitter-mike的数据库宝典-<COLOR>.svg)](https://twitter.com/mikesdatawork?lang=en)
[![Wordpress](https://img.shields.io/badge/Wordpress-mike的数据库宝典-<COLOR>.svg)](https://mikesdatawork.wordpress.com/)

---
## License
[![LicenseCCSA](https://img.shields.io/badge/License-CreativeCommonsSA-<COLOR>.svg)](https://creativecommons.org/share-your-work/licensing-types-examples/)

![Lee Songming](https://raw.githubusercontent.com/LiCongMingDeShujuku/git-resources/master/1-clever-data-github.png "李聪明的数据库")

