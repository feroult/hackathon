# hackathon

# extract data

resize

`
for foo in `ls *.jpg | cut -d \. -f 1`; do convert $foo.jpg -resize 50x50\! -quality 100 data/$foo.jpg; done
`

extract rgb

`
for foo in `ls *.jpg | cut -d \. -f 1`; do convert $foo.jpg txt/$foo.txt ; done
`

create dataset

`
for foo in `ls *.txt | cut -d \. -f 1`; do echo "$foo - $(tail -n +2 $foo.txt  | cut -d " " -f 2 | cut -c2- | rev | cut -c2- | rev  | tr '\n' ',')$(grep $foo\, labels.csv | cut -d "," -f 2)"; done > dataset.csv
`
