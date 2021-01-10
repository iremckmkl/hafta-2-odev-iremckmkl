# 1980’den itibaren herhangi bir spor grubunda üst üste 3 veya daha fazla madalya almış atletleri bulalım.

``` SQL
select Athlete,Sport, Medalnum
FROM (select sport,country,count(1) as medalnum,athlete
      from `dsmbootcamp.irem_cakmakli.summer_medals` 
      where medal is not null and year >= 1980 
      group by sport,Country,athlete
      order by sport,medalnum desc)
where medalnum >3

```
