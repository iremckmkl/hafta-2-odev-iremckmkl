###Soru 1) 1980’den itibaren spor grubu bazında en çok madalya alan 1. 3. 5. ülkeyi bulalım.

``` SQL 

select sport,
lead(country,0) over (partition by sport order by medalnum desc) as first_country,
lead(country,2) over (partition by sport order by medalnum desc) as third_country,
lead(country,4) over (partition by sport order by medalnum desc) as fifth_country,
from (select sport,country,count(1) as medalnum
      from `dsmbootcamp.irem_cakmakli.summer_medals` 
      where medal is not null and year >= 1980 
      group by sport,Country
      order by sport,medalnum desc)
group by sport,country,medalnum         
order by medalnum desc

```

