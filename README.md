# parlezVousTreason
Metadata analysis identifying video files with potential evidence of the 1/6/2021 raid on the US capitol

I took the large archive of metadata json files, and narrowed it down to only those which have GPS metadata
The way I did that was kludgy, so there are a lot of duplicates; I found all the files with GPSCoordinates, and then separately found all the files with GPSPosition . Many had both, but not all. 

I used sed to change the format of the data (get rid of spaces, add degree signs rather than the characters deg)
$ sed 's/ deg /°/g' fileName
and
$ sed "s/' /'/g" fileName

I used grep to narrow down gps coordinates close to the heart of the action. 
The commands used were: 

$ grep "77°0" ./gpsMetadata.txt | grep "38°53'[10-40]" > ./gpsMetadataOnlyCapitol.txt

and

$ grep "77°[0-2]" ./gpsMetadata.txt | grep "38°53'[3-60]" > ./gpsMetadataWHToCapitol.txt

I have very little regex experience, so I wouldn't be surprised if I messed something up there; if you know better, please double check
